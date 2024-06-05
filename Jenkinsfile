pipeline {
    agent any

    stages {
        stage('i211216 Checkout') {
            steps {
                sh 'git --version'
                git credentialsId: 'github-credentials-pat', url: 'https://github.com/NUCESFAST/scd-final-lab-exam-haadiyeah.git'
            }
        }

        stage('i211216 Build Docker images') {
            steps {
                sh 'docker-compose build'
            }
        }

        stage('i211216 Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials-pat', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                }
            }
        }

        stage('i211216 Push Docker images') {
            steps {
                sh 'docker-compose push'
            }
        }
    }
}