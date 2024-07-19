
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
                    bat 'docker build -t my_vol .'
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    bat 'docker run -d --name myimage_1 -p 8020:80 my_vol'
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
