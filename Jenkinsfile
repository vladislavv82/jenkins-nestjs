pipeline {
    agent {
        docker { image 'node:20.11.1-alpine3.19' }
    }
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
                sh "nest --version"

            }
        }

        stage('Start Application') {
            steps {
                sh "yarn start:dev"
            }
        }
    }
}
