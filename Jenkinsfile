pipeline {
    agent any

    environment {
        DOCKER_REGISTRY_CREDENTIALS = 'your-registry-credentials'
        DOCKER_REGISTRY_URL = 'your-docker-registry-url'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/DaoOfDreams/basic-node-backend.git'
            }
        }

        stage('Build and Test') {
            steps {
                sh 'npm install'
                sh 'npm test'
            }
        }

        stage('Dockerize') {
            steps {
                script {
                    docker.build('basic-node-backend', '.')
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry(DOCKER_REGISTRY_URL, DOCKER_REGISTRY_CREDENTIALS) {
                        docker.image('basic-node-backend').push()
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                // Add your deployment steps here, e.g., Kubernetes deployment, Docker Swarm deployment, etc.
                // You can also use SSH to deploy the container manually to a remote server
            }
        }
    }
}
