 pipeline {
    agent any

    environment {
        DOCKERHUB_USERNAME = 'sravankumar0338'
        DOCKERHUB_PASSWORD = 'Kumar@1997'
        DOCKER_IMAGE = 'my-docker-image'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch : 'main', url: 'https://github.com/Kumarazdevops/project-pipeline-1.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    //docker.build(DOCKER_IMAGE)
                    bat 'docker build -t my-docker-image .'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    docker.image(DOCKER_IMAGE).inside {
                        sh 'make test'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS_ID) {
                        docker.image(DOCKER_IMAGE).push('latest')
                    }
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
