pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-username/my-python-app.git'
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