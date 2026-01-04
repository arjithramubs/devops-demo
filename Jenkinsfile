pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                pm2 stop devops-demo || true
                pm2 delete devops-demo || true
                pm2 start app.js --name devops-demo
                '''
            }
        }
    }
}
