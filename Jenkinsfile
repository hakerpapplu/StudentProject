pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "hakerpapplu/studentproject:latest"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git credentialsId: '1b6a864c-fa5e-4ae2-a102-55d7e04784e8', branch: 'main', url: 'https://github.com/hakerpapplu/StudentProject.git'
            }
        }
    }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $DOCKER_IMAGE .'
                }
            }
        }

        stage('Login to Docker Hub') {
            steps {
                script {
                    withDockerRegistry([credentialsId: 'docker-hub-credentials', url: '']) {
                        sh 'docker login -u your-dockerhub-username -p $DOCKER_PASSWORD'
                    }
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
    }
}