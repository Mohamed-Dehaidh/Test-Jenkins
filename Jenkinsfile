pipeline {
    agent any

    environment {
        CREDENTIALS_ID = "dockerhub-UP"
    }

    stages {
        stage('Build and Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: env.CREDENTIALS_ID, usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh '''
                        docker build -t Mohamed-Dehaidh/dockerfile:latest .
                        docker login -u "$USERNAME" -p "$PASSWORD"
                        docker push Mohamed-Dehaidh/dockerfile:latest
                    '''
                }
            }
        }
    }
}
