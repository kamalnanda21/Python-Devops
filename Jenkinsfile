pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: 'github-pat', url: 'https://github.com/kamalnanda21/Python-Devops.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("my-python-image")
                }
            }
        }

        stage('Run in Docker') {
            steps {
                script {
                    dockerImage.run()
                }
            }
        }
    }
}