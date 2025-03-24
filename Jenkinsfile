pipeline {
    agent any
    environment {
        DOCKER_IMAGE = "hakerpapplu/studentproject"
    }
    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/hakerpapplu/StudentProject.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub-credentials', url: '']) {
                    sh 'docker login -u your-dockerhub-username -p your-dockerhub-password'
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }
    }
}

