pipeline {
    agent any

    stages {
        stage('i211216 Checkout') {
            steps {
                sh 'echo "i21-1216 Checking out code"'
                git credentialsId: 'github-credentials-pat', url: 'https://github.com/yourusername/yourrepository.git'
            }
        }

        stage('i211216 Build Docker images') {
            steps {
                sh 'echo "i21-1216 Building Docker images"'
                sh 'docker-compose build'
            }
        }

        stage('i211216 Login to DockerHub') {
            steps {
                sh 'echo "i21-1216 Logging in to DockerHub"'
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                }
            }
        }

        stage('i211216 Push Docker images') {
            steps {
                sh 'echo "i21-1216 Pushing Docker images"'
                sh 'docker-compose push'
            }
        }
    }
}