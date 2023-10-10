pipeline {
    agent any

    environment {
        // Имя учетных данных AWS S3, которые вы создали ранее
        S3_CREDENTIALS = credentials('Jenkins-cred')
    }
    stage('Upload to S3') {
    steps {
        dir('/путь/к/вашей/директории') {
            script {
                s3Upload(path: '**/*', bucket: 'katsko-bucket', includePathPattern: './*', region: 'eu-north-1')
            }
        }
    }
}

}


