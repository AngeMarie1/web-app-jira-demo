pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'AngeMarie/my-web-app'     // Change to your Docker Hub repo
        DOCKER_CREDENTIALS_ID = 'docker-hub-credentials'   // Jenkins credentials ID
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image using Jenkins Docker plugin
                    dockerImage = docker.build("${DOCKER_IMAGE}:latest")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    // Authenticate + Push docker image
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS_ID) {
                        dockerImage.push('latest')
                    }
                }
            }
        }
    }
}
