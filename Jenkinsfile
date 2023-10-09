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

                    // Параметры S3-бакета
                    def s3Bucket = 'your-s3-bucket-name'
                    def s3ObjectKey = 'path/to/your/file/in/s3.txt' // Путь, по которому будет загружен файл в S3

                    // Путь к локальному файлу, который нужно загрузить
                    def localFilePath = 'path/to/your/local/file.txt'

                    // Загрузка файла в S3
                    withAWS(credentials: awsCredentials, region: 'us-east-1') {
                        sh "aws s3 cp ${localFilePath} s3://${s3Bucket}/${s3ObjectKey}"
                    }
                }
            }
        }
    }
}

