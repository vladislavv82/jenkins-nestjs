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
                sh "docker --version"
            }
        }

        stage('Start Application') {
            steps {
                sh "yarn start:dev"
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('my-node-app')
                }
            }
    }
}
