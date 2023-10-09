pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps work too"
                    ls -lah
                '''
            }
        }

        stage('Upload to AWS') {
            steps {
                script {
                    def awsRegion = 'eu-north-1'
                    def s3Bucket = 'katsko-bucket'

                    // Получаем список файлов и подпапок из текущего каталога репозитория
                    def filesToUpload = sh(script: 'ls -1', returnStdout: true).trim().split('\n')

                    // Загружаем каждый файл на S3 Bucket
                    withAWS(region: awsRegion, credentials: 'jenkins-credentials') {
                        for (file in filesToUpload) {
                            def s3ObjectKey = "artifacts/${file}" // Формируем ключ объекта на S3
                            s3Upload(path: s3ObjectKey, bucket: s3Bucket, source: file)
                        }
                    }
                }
            }
        }
    }
}

