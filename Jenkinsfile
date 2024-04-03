pipeline {
    agent any
    
    stages {
        stage('Echo Notification') {
            steps {
                echo 'Начало выполнения pipeline'
            }
        }    
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh "yarn"
            }
        }

        stage('Start Application') {
            steps {
                sh "yarn start"
            }
        }
    }
}
