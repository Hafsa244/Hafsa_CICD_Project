pipeline {
    agent any

    environment {
        IMAGE = "hafsa244/cicd-project"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Hafsa244/Hafsa_CICD_Project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${IMAGE}:${BUILD_NUMBER}")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub-cred') {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}