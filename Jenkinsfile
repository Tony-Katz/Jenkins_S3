pipeline {
    agent any

    environment {
        // Имя учетных данных AWS S3, которые вы создали ранее
        S3_CREDENTIALS = credentials('Jenkins-cred')
    }

    stages {
        stage('Upload to S3') {
            steps {
                script {
                    // Определите файлы и папки для загрузки в S3 bucket
                    def s3Entries = [
                        [sourceFile: '**/*']
                    ]
                    // Выполнение плагина S3 Publisher с использованием профиля и настройками
                    s3BucketPublish(profileName: 'Jenkins-cred', entries: s3Entries)
                }
            }
        }
    }
}

