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
                    def dockerImage = docker.build("kamal-python-image")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    docker.image("kamal-python-image").run()
                }
            }
        }
    }
}