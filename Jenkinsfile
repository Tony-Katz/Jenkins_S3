pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Upload to S3') {
            steps {
                script {
                    def s3UploadOpts = [
                        path: '', // Ваш путь к файлам для загрузки
                        bucket: 'katsko-bucket',
                        includePathPattern: './*',
                        region: 'eu-north-1',
                        credentials: [
                            awsAccessKeyId: credentials('Jenkins-credentials').AWS_ACCESS_KEY_ID,
                            awsSecretKey: credentials('Jenkins-credentials').AWS_SECRET_ACCESS_KEY
                        ]
                    ]

                    s3Upload(s3UploadOpts)
                }
            }
        }
    }
}

