pipeline {
    agent any

    environment {
        CREDENTIALS_ID = "dockerhub-UP"
        DOCKER_IMAGE_NAME = "mohameddehaidh/test-image"
    }

    stages {
        stage('Build and Push Docker Image') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: env.CREDENTIALS_ID, usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                        sh """
                            docker build -t ${env.DOCKER_IMAGE_NAME}:latest .
                            echo "build done!##########################"
                            docker login -u "${USERNAME}" -p "${PASSWORD}"
                            echo "login done!!#########################"
                            docker push ${env.DOCKER_IMAGE_NAME}:latest
                            echo "push done############################"
                        """
                    }
                }
            }
        }
    }

    post {
        always {
            sh 'docker logout'
            cleanWs()
        }
    }
}
