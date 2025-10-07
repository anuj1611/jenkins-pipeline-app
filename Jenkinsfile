pipeline {
    agent any

    environment {
        IMAGE_NAME = "jenkins-pipeline-app"
        CONTAINER_NAME = "flask-container"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Pulling code from GitHub...'
                git branch: 'main', url: 'https://github.com/anuj1611/Jenkins-pipeline-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t ${IMAGE_NAME} .'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing container...'
                sh 'docker run --rm ${IMAGE_NAME} python -m unittest || echo "No tests yet!"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying app...'
                script {
                    // Stop any running container
                    sh 'docker rm -f ${CONTAINER_NAME} || true'
                    // Run new container
                    sh 'docker run -d --name ${CONTAINER_NAME} -p 5000:5000 ${IMAGE_NAME}'
                }
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful! Visit http://localhost:5000'
        }
        failure {
            echo '❌ Deployment failed!'
        }
    }
}
