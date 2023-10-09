pipeline {
    agent any

    environment {
        PATH = "/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/path/to/awscli:$PATH"
    }

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
        stage('Upload to AWS S3') {
            steps {
                sh 'aws s3 cp . s3://katsko-bucket/ --recursive --region eu-north-1'
            }
        }
    }
}

