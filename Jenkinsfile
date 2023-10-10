pipeline {
    agent any

    environment {
        // Имя учетных данных AWS S3, которые вы создали ранее
        S4_CREDENTIALS = credentials('Jenkins-cred')
    }

    stages {
        stage('Upload to S3') {
            steps {
                script {
                    s3Upload(path: '', bucket: 'katsko-bucket', includePathPattern: './*', region: 'eu-north-1', credentials: S3_CREDENTIALS)
                }
            }
        }
    }
}

