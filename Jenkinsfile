pipeline {
    agent any

    tools {
        nodejs "NodeJS-20"
    }

    stages {

        stage('Checkout') {
            steps {
                echo "Pulling code from GitHub..."
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                dir('my-app') {
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                dir('my-app') {
                    echo "Building React app..."
                    sh 'npm run build'
                }
            }
        }

        stage('Test') {
            steps {
                dir('my-app') {
                    echo "Running tests..."
                    sh 'npm test -- --watchAll=false --passWithNoTests'
                }
            }
        }

        stage('Deploy') {
            steps {
                dir('my-app') {
                    echo "Deploying React app..."
                }
            }
        }
    }

    post {
        success {
            echo "React pipeline executed successfully!"
        }

        failure {
            echo "React pipeline failed!"
        }
    }
}