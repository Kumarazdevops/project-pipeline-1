
pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'my_image:latest'
        DOCKERHUB_USERNAME = 'sravankumar0338'
        DOCKERHUB_PASSWORD = 'Kumar@1997'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch : 'main', url: 'https://github.com/Kumarazdevops/project-pipeline-1.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t my_image .'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    bat 'docker volume create vol1'
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
