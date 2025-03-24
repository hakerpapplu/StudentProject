pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "hakerpapplu/studentproject:latest"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git credentialsId: '53d25c8d-d37a-4193-a476-951cd3a163ae', branch: 'main', url: 'https://github.com/hakerpapplu/StudentProject.git'
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