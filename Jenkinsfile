pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the repository from Git
                git url: 'https://github.com/AdhibanGanesh/node-api.git', branch: 'master'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                // Install required dependencies
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image for the app
                    sh 'docker build -t node-api .'
                }
            }
        }

        stage('Run Tests') {
            steps {
                // Placeholder for tests (add your own tests here)
                echo 'Running tests...'
            }
        }

        stage('Deploy Container') {
            steps {
                // Run the Docker container
                sh 'docker run -d -p 3000:3000 --name node-api node-api'
            }
        }
    }

    post {
        always {
            // Clean up by removing the Docker container and image
            sh 'docker rm -f node-api || true'
            sh 'docker rmi node-api || true'
        }
    }
}