pipeline {
    agent any

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


        stage('Deploy') {
            steps {
                // Add your deployment steps here, e.g., Kubernetes deployment, Docker Swarm deployment, etc.
                // You can also use SSH to deploy the container manually to a remote server
            }
        }
    }
}

