stage('Docker Build & Push') {
    steps {
        script {
            echo "Building Docker image..."

            def dockerImage = "YOUR_DOCKERHUB_USERNAME/web-app-jira-demo:latest"

            // Login to Docker Hub
            withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                sh "echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin"
            }

            // Build image
            sh "docker build -t ${dockerImage} ."

            // Push image
            sh "docker push ${dockerImage}"

            echo "Docker image pushed successfully: ${dockerImage}"
        }
    }
}
