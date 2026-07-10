pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo "Repository checked out successfully"
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker compose up -d'
            }
        }
    }
}
