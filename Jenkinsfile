pipeline {
    agent any

    environment {
        // Имя учетных данных AWS S3, которые вы создали ранее
        S3_CREDENTIALS = credentials('jenkins-credentials')
    }

    stages {
        stage('Checkout') {
            steps {
                // Вы можете добавить этап загрузки исходного кода из Git репозитория, если это необходимо
                // Например, используя 'checkout scm' или другие методы
            }
        }

        stage('Upload to S3') {
            steps {
                script {
                    // Загрузка всех файлов и папок из текущей локальной директории в корневую директорию S3 bucket
                    s3Upload(includePathPattern: '*', bucket: 'katsko-bucket', credentials: env.S3_CREDENTIALS, region: 'eu-north-1')
                }
            }
        }
    }
}

