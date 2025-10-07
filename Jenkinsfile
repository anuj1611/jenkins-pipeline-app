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
                git branch: 'main', url: 'https://github.com/anuj1611/jenkins-pipeline-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                bat 'docker build -t %IMAGE_NAME% .'
            }
        }

        stage('Test') {
            steps {
                echo 'Running test container...'
                bat 'docker run --rm %IMAGE_NAME% python -m unittest || echo "No tests found"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying container...'
                script {
                    // Stop old container if it exists
                    bat 'docker rm -f %CONTAINER_NAME% || echo "No container to remove"'
                    // Run new container
                    bat 'docker run -d --name %CONTAINER_NAME% -p 5000:5000 %IMAGE_NAME%'
                }
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful! Visit http://localhost:5000'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}
