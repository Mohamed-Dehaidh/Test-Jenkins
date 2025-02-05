pipeline {
    agent any

    environment {
        CREDENTIALS_ID = "jenkins-UP" // Or your registry credentials ID
        DOCKER_IMAGE_NAME = "Mohamed-Dehaidh/Test-Jenkins/Test-image" // Update with your details
        DOCKER_IMAGE_TAG = "latest" // Or a specific tag like build number
    }

    stages {
        stage('Build and Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: env.CREDENTIALS_ID, usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh '''
                        docker build -t "${env.DOCKER_IMAGE_NAME}:${env.DOCKER_IMAGE_TAG}" .
                        docker login -u "$USERNAME" -p "$PASSWORD"
                        docker push "${env.DOCKER_IMAGE_NAME}:${env.DOCKER_IMAGE_TAG}"
                    '''
                }
            }
        }
    }
}
