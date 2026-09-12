pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Validate HTML') {
            steps {
                sh '''
                    echo "Checking website files..."

                    test -f index.html

                    echo "index.html found"
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    echo "Deploying website..."

                    sudo rsync -av --delete \
                    --exclude='.git' \
                    ./ /var/www/mywebsite/

                    echo "Deployment completed"
                '''
            }
        }
    }

    post {
        success {
            echo 'Website deployed successfully!'
        }

        failure {
            echo 'Website deployment failed!'
        }
    }
}