pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo '📥 Cloning repository from GitHub...'
            }
        }

        stage('Build') {
            steps {
                echo '🔨 Building application...'

                sh '''
                if [ -f app/index.html ]; then
                    echo "Build Successful: index.html found"
                else
                    echo "Build Failed"
                    exit 1
                fi
                '''
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running tests...'

                sh '''
                grep "Jenkins CI/CD Pipeline Working Successfully" app/index.html
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying application...'

                sh '''
                mkdir -p deployment
                cp -r app/* deployment/
                echo "Deployment Successful"
                '''
            }
        }
    }
}