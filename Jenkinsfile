pipeline {
    agent any

    environment {
        APP_NAME = "Sample Node App"
    }

    stages {

        stage('Checkout Code') {
            steps {
                echo "Cloning repository..."
                git branch: 'main', url: 'https://github.com/manjub-git-hub/sample-node-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo "Installing dependencies..."
                sh 'npm install || echo "No dependencies to install"'
            }
        }

        stage('Testing') {
            steps {
                echo "Running tests..."
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                echo "Building application..."
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application..."
                sh '''
                  mkdir -p /tmp/sample-deploy
                  cp app.js /tmp/sample-deploy/
                  echo "Deployment completed"
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline executed successfully!"
        }
        failure {
            echo "❌ Pipeline failed. Check logs."
        }
    }
}
