pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = "eu-north-1"
        THE_BUTLER_SAYS_SO = credentials('Jenkins-credentials')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building stage"
            }
        }

        stage('Test') {
            steps {
                echo "Testing stage"
            }
        }

        stage('Deploy to S3') {
            steps {
                echo "Deploying"
                sh 'aws s3 cp ./ s3://katsko-bucket/ --recursive'
            }
        }
    }

    post {
        success {
            echo "Success"
        }
        failure {
            echo "Failure"
        }
    }
}

