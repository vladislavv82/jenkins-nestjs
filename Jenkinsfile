pipeline {
    agent any
    
    tools {nodejs 'nodejs jenkins'}
    
    stages {
        
        stage('Echo Notification') {
            steps {
                echo 'Начало выполнения pipeline 🚀'
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
                dir('lesson-1') {
                    sh 'docker build -t nest-js/jenkins-images:latest .'
                }
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
