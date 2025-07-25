pipeline {
    agent any

    environment {
        IMAGE_NAME = "kamal-python-app-image"
        IMAGE_TAG = "${BUILD_NUMBER}"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'github-pat', url: 'https://github.com/kamalnanda21/Python-Devops.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    def fullImageName = "${IMAGE_NAME}:${IMAGE_TAG}"
                    echo "Building Docker image: ${fullImageName}"
                    docker.build(fullImageName)
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    def fullImageName = "${IMAGE_NAME}:${IMAGE_TAG}"
                    echo "Running Docker image: ${fullImageName}"
                    docker.image(fullImageName).run()
                }
            }
        }
    }
}