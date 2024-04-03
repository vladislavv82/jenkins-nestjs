pipeline {
    agent any

    environment {
    }

    stages {
        stage('Send Email Notification') {
            steps {
                emailext body: 'Начало выполнения pipeline', 
                         recipientProviders: [developers()], 
                         subject: 'Уведомление о начале выполнения pipeline',
                         to: 'vladislav.akopian82@gmail.com'
            }
        }
    }
}
