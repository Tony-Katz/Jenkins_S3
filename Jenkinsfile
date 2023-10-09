pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Клонирование репозитория (замените URL вашего репозитория)
                checkout scm
            }
        }

        stage('Upload to S3') {
            steps {
                script {
                    // Имя учетных данных AWS S3, которые вы создали ранее
                    def awsCredentials = credentials('jenkins-credentials')

                    // Путь к локальному файлу, который нужно загрузить
                    def localFilePath = './*'

                    // Загрузка файла в S3
                    s3Upload(file: localFilePath, bucket: 'your-s3-bucket-name', path: 'path/to/your/file/in/s3.txt', credentials: awsCredentials)
                }
            }
        }
    }
}

