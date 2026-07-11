pipeline {

    agent any

    options {
        timestamps()
    }

    stages {

        stage('Workspace Information') {
            steps {
                echo "Current Workspace Information"
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker Image..."
                sh 'docker compose build'
            }
        }

        stage('Deploy Application') {
            steps {
                echo "Stopping old containers (if any)..."

                sh '''
                docker compose down || true
                '''

                echo "Starting latest application..."

                sh '''
                docker compose up -d --build
                '''
            }
        }

        stage('Deployment Verification') {
            steps {
                echo "Checking running containers..."

                sh 'docker ps'

                echo "Checking application..."

                sh 'docker compose ps'
            }
        }

    }

    post {

        success {
            echo "========================================="
            echo "CI/CD Pipeline Completed Successfully!"
            echo "Application Deployed Successfully."
            echo "========================================="
        }

        failure {
            echo "========================================="
            echo "CI/CD Pipeline Failed!"
            echo "Please check the Console Output."
            echo "========================================="
        }

        always {
            echo "Pipeline Execution Finished."
        }

    }

}
