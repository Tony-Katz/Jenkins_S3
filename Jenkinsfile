pipeline {
    agent any

    environment {
        // Имя учетных данных AWS S3, которые вы создали ранее
        S3_CREDENTIALS = credentials('Jenkins-credentials')
    }

    stages {
        stage('Upload to S3') {
            steps {
                // Загрузка файлов из репозитория GitHub в корневую папку S3
                script {
                    def s3Bucket = 'katsko-bucket' // Укажите имя вашего S3 бакета
                    def s3Path = '/' // Используйте '/' для загрузки в корневую папку

                    s3Upload(
                        bucket: s3Bucket,
                        includePathPattern: '**/*',
                        path: s3Path,
                        credentials: env.S3_CREDENTIALS,
                        region: 'eu-north-1'
                    )
                }
            }
        }
    }
}

