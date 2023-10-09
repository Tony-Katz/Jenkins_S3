pipeline {
    agent any

    environment {
        // Имя учетных данных AWS S3, которые вы создали ранее
        S3_CREDENTIALS = credentials('jenkins-credentials')
    }

    stages {
        stage('Upload to S3') {
            steps {
                // Загрузка файлов из репозитория GitHub в S3
                script {
                    s3Upload(includePathPattern: '**/*', bucket: 'your-s3-bucket-name', path: 'path/to/your/files/in/s3/', credentials: env.S3_CREDENTIALS)
                }
            }
        }
    }
}

