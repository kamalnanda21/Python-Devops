pipeline {
    agent any

    environment {
        IMAGE_NAME = "kamal-python-app-image"
        CONTAINER_NAME = "kamal-python-container"
        HOST_PORT = "3333"
        CONTAINER_PORT = "5000"
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
                    def fullImageName = "${IMAGE_NAME}"  // No tag means default is ":latest"
                    echo "Building Docker image: ${fullImageName}"
                    docker.build(fullImageName)
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    def fullImageName = "${IMAGE_NAME}"  // No tag used
                    echo "Running Docker container: ${CONTAINER_NAME} from image: ${fullImageName}"

                    // Stop and remove existing container with the same name
                    sh """
                        docker rm -f ${CONTAINER_NAME} || true
                        docker run -d --name ${CONTAINER_NAME} -p ${HOST_PORT}:${CONTAINER_PORT} ${fullImageName}
                    """
                }
            }
        }
    }
}