pipeline {
    agent any
    
    tools {
        nodejs 'nodejs jenkins'
    }
    
    stages {
        
        stage('Echo Notification') {
            steps {
                echo 'Начало выполнения pipeline 🚀'
            }
        }

        stage('Docker version') {
            steps {
                sh 'docker version'
            }
        }
        
        stage('Delete workspace before build starts') {
            steps {
                echo 'Deleting workspace'
                deleteDir()
            }
        }
        
        stage('Checkout') {
            steps{
                git branch: 'main',
                    url: 'https://github.com/vladislavv82/jenkins-nestjs.git'        
                }
        }

        stage('Install Dependencies') {
            steps {
                sh "yarn"
                sh "nest --version"
            }
        }

        stage('Build docker image') {
            steps{
                sh 'docker build -t nest-js/jenkins-images:latest .'
            }
        }
        
        stage('Push docker image to DockerHub') {
            steps{
                withDockerRegistry(credentialsId: 'docker-hub', url: 'https://index.docker.io/v1/') {
                    sh '''
                        docker push nest-js/jenkins-images:latest
                    '''
                }
            }
        }
        
        stage('Delete docker image locally') {
            steps{
                sh 'docker rmi nest-js/jenkins-images:latest'
            }
        }
    }
}
