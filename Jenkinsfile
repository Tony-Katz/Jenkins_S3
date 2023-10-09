pipeline {
    agent any

    environment {
        // Имя учетных данных AWS S3, которые вы создали ранее
        S3_CREDENTIALS = credentials('jenkins-credentials')
    }

    stages {
        stage('Upload to S3') {
            steps {
                // Загрузка файлов из текущей директории в S3
                script {
                    s3Upload(path: '**/*', bucket: 'katsko-bucket', includePathPattern: './*', region: 'eu-north-1')
                }
            }
        }
    }
}

