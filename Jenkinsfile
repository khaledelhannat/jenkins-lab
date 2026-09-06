pipeline {
    agent any

    environment {
        IMAGE = 'localhost:5000/my-app'
        TAG = "${BUILD_NUMBER}"
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Code was checked out by Jenkins.'
            }
        }

        stage('Test') {
            steps {
                sh '''
                    echo "Running tests..."
                    test -f app/index.html
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                    docker build \
                    -t ${IMAGE}:${TAG} \
                    .
                '''
            }
        }

        stage('Push Docker Image') {
            steps {
                sh '''
                    docker push ${IMAGE}:${TAG}
                '''
            }
        }
    }
    
}


