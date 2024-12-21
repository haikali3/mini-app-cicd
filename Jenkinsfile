pipeline {
    agent any

    environment {
        DOCKER_COMPOSE_FILE = 'docker-compose.yml'
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the repository
                git branch: 'main', url: 'https://github.com/haikali3/mini-app-cicd.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                script {
                    // Build backend and frontend images
                    sh 'docker-compose build'
                }
            }
        }

        stage('Test Backend') {
            steps {
                script {
                    // Run backend container and test API
                    sh '''
                    docker run -d --rm --name backend-test -p 3000:3000 mini-app-cicd_backend
                    sleep 5
                    curl -f http://localhost:3000 || exit 1
                    docker stop backend-test
                    '''
                }
            }
        }

        stage('Test Frontend') {
            steps {
                script {
                    // Run frontend container and test HTTP access
                    sh '''
                    docker run -d --rm --name frontend-test -p 8000:80 mini-app-cicd_frontend
                    sleep 5
                    curl -f http://localhost:8000 || exit 1
                    docker stop frontend-test
                    '''
                }
            }
        }

        stage('Deploy Application') {
            steps {
                script {
                    // Deploy the application using docker-compose
                    sh 'docker-compose down || true'
                    sh 'docker-compose up -d'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution complete!'
        }
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
