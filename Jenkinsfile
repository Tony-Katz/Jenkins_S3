pipeline {
    agent any

    environment {
        // Имя учетных данных AWS S3, которые вы создали ранее
        S3_CREDENTIALS = credentials('Jenkins-cred')
    }

    stages {
        stage('Upload to S3') {
            steps {
                // Загрузка файлов из текущей директории в корень S3 bucket
                script {
                    s3Upload(path: '.', bucket: 'katsko-bucket', includePathPattern: '**/*', region: 'eu-north-1')
                }
            }
        }
    }
}

