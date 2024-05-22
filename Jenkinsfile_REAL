pipeline {
    agent any
    tools {
        jdk 'JDK-my'
        maven 'maven3'
    }
    
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', credentialsId: '073e6c59-a26b-42e1-ae69-7f8060073a97', url: 'https://github.com/Airej/mevan-Ekart.git'
            }
        }
        
        stage('Compile') {
            steps {
                sh "mvn clean compile -DskipTest=true"
            }
        }
        
        stage('OWASP Scan') {
            steps {
                dependencyCheck additionalArguments: '--scan ./ ', odcInstallation: 'DP'
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
        
        stage('Sonarqube') {
            steps {
                
                withSonarQubeEnv('sonar-server'){
                   sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Shopping-Cart \
                   -Dsonar.java.binaries=. \
                   -Dsonar.projectKey=Shopping-Cart '''
                }
            }
        }
        
        stage('Build') {
            steps {
                sh "mvn clean package -DskipTests=true"
            }
        }
        
        stage('Docker Build & Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: '5a8a02d9-243d-4ec3-9bf1-be901cab1a65', toolName: 'docker') {
                        
                        sh "docker build -t shopping-cart -f docker/Dockerfile ."
                        sh "docker tag  shopping-cart airej/shopping-cart:latest"
                        sh "docker push airej/shopping-cart:latest"
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    withDockerRegistry(credentialsId: '5a8a02d9-243d-4ec3-9bf1-be901cab1a65', toolName: 'docker') {
                        
                        sh "docker run -d --name shop-shop -p 8070:8070 airej/shopping-cart:latest"
                    }
                }
            }
        }
    }
}
