pipeline {
    agent any

    environment {
        // Имя учетных данных AWS S3, которые вы создали ранее
        S3_CREDENTIALS = credentials('Jenkins-credentials')
    }

    stages {
        stage('Upload to S3') {
            steps {
                // Загрузка файлов из репозитория GitHub в S3
                script {
			s3Upload(includePathPattern: '**/*', bucket: 'katsko-bucket', path: './*', credentials: env.S3_CREDENTIALS, region: 'eu-north-1')
                }
            }
        }
    }
}

