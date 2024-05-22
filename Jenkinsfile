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
        stage('Changing App Setting files for PRE-PROD env') {
            steps {
                sh "echo 'Hello' "
                sleep 50
                //git branch: 'main', credentialsId: '073e6c59-a26b-42e1-ae69-7f8060073a97', url: 'https://github.com/Airej/mevan-Ekart.git'
            }
        }
        
        stage('Changing App Setting files for PROD env') {
            steps {
                sh "echo 'Hello' "
                sleep 50
                //sh "mvn clean compile -DskipTests=true"
            }
        }
        
        stage('Cleaning and restoring solutions') {
            steps {
                sh "echo 'Hello' "
                sleep 50
                //dependencyCheck additionalArguments: '--scan ./', odcInstallation: 'DP'
                //dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
        stage('Building solutions') {
            steps {
                sh "echo 'Hello' "
                sleep 50
                //dependencyCheck additionalArguments: '--scan ./', odcInstallation: 'DP'
                //dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
        
        stage('Deployment on K8s Cluster') {
            parallel {
                stage('Building.tagging.pushing and deploying Aggregation') {
                    steps {
                        sh "echo 'Hello from Parallel Stage 1'"
                    }
                }
                stage('Building.tagging.pushing and deploying Documentation') {
                    steps {
                        sh "echo 'Hello from Parallel Stage 2'"
                    }
                }
                stage('Building.tagging.pushing and deploying Finance') {
                    steps {
                        sh "echo 'Hello from Parallel Stage 3'"
                    }
                }
                stage('Building.tagging.pushing and deploying API gateways') {
                    steps {
                        sh "echo 'Hello from Parallel Stage 4'"
                    }
                }
                stage('Building.tagging.pushing and deploying Identification') {
                    steps {
                        sh "echo 'Hello from Parallel Stage 5'"
                    }
                }
                stage('Building.tagging.pushing and deploying Operations') {
                    steps {
                        sh "echo 'Hello from Parallel Stage 5'"
                    }
                }
                stage('Building.tagging.pushing and deploying Regix') {
                    steps {
                        sh "echo 'Hello from Parallel Stage 5'"
                    }
                }
                stage('Building.tagging.pushing and deploying Apigee lint') {
                    steps {
                        sh "echo 'Hello from Parallel Stage 5'"
                    }
                }
                stage('Building.tagging.pushing and deploying Openshift') {
                    steps {
                        sh "echo 'Hello from Parallel Stage 5'"
                    }
                }
                stage('Building.tagging.pushing and deploying Email') {
                    steps {
                        sleep 50
                        sh "echo 'Hello from Parallel Stage 5'"
                    }
                }
            }

            // Commented out steps
            // script {
            //     // withSonarQubeEnv('sonar-server') {
            //     //     sh ''' $SCANNER_HOME/bin/sonar-scanner \
            //     //         -Dsonar.projectName=Shopping-Cart \
            //     //         -Dsonar.java.binaries=. \
            //     //         -Dsonar.projectKey=Shopping-Cart '''
            //     // }
            // }
        }
        
        stage('Publishing solutions on web') {
            steps {
                sh "echo 'Hello' "
                sleep 50
                //sh "mvn clean package -DskipTests=true"
            }
        }
        
        stage('Balancing load on web') {
            steps {
                sh "echo 'Hello' "
                sleep 50
                // Commented out steps
                // script {
                //     // withDockerRegistry(credentialsId: '5a8a02d9-243d-4ec3-9bf1-be901cab1a65', toolName: 'docker') {
                //     //     sh "docker build -t shopping-cart -f docker/Dockerfile ."
                //     //     sh "docker tag shopping-cart airej/shopping-cart:latest"
                //     //     sh "docker push airej/shopping-cart:latest"
                //     // }
                // }
            }
        }

        stage('Deployed') {
            steps {
                sh "echo 'Hello' "
                // Commented out steps
                // script {
                //     // withDockerRegistry(credentialsId: '5a8a02d9-243d-4ec3-9bf1-be901cab1a65', toolName: 'docker') {
                //     //     sh "docker run -d --name shop-shop -p 8070:8070 airej/shopping-cart:latest"
                //     // }
                // }
            }
        }
    }
}

