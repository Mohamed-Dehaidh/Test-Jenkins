pipeline {
    agent any

    environment {
        DOCKER_IMAGE_NAME = "mohameddehaidh/Dockerfile"
        DOCKER_CREDENTIALS_ID = "dockerhub-UP"
    }

    stages {
        stage('Build and Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: env.DOCKER_CREDENTIALS_ID, usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh '''
                        docker build -t "${env.DOCKER_IMAGE_NAME}:latest"
                        docker login -u "$USERNAME" -p "$PASSWORD"
                        docker push "${env.DOCKER_IMAGE_NAME}:latest"
                    '''
                }
            }
        }
    }
}
