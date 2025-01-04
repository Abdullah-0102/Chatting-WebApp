pipeline {
    agent any
    environment {
        DOCKER_HUB_CREDENTIALS = credentials('abdullah2204')
    }
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Abdullah-0102/Chatting-WebApp.git'
            }
        }
        stage('Build Backend Docker Image') {
            steps {
                sh 'docker build -t abdullah2204/testing-chatting-webapp-jenkins-backend -f server/Dockerfile ./server || exit 1'
            }
        }
        stage('Build Frontend Docker Image') {
            steps {
                sh 'docker build -t abdullah2204/testing-chatting-webapp-jenkins-frontend -f public/Dockerfile ./public || exit 1'
            }
        }
        stage('Push Docker Images') {
            steps {
                withDockerRegistry([credentialsId: 'abdullah2204', url: 'https://index.docker.io/v1/']) {
                    sh 'docker push abdullah2204/testing-chatting-webapp-jenkins-backend'
                    sh 'docker push abdullah2204/testing-chatting-webapp-jenkins-frontend'
                }
            }
        }
    }
    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}