pipeline {

    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'pwd'
                sh 'ls -la'
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
