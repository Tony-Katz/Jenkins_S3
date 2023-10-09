pipeline {
    agent any
    
    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                sh 'echo Hello World'
                sh 'echo Multiline shell steps work too'
                sh 'ls -lah'
            }
        }
        
        stage('Upload to AWS S3') {
            steps {
                script {
                    def awsCliPath = sh(script: 'which aws', returnStdout: true).trim()
                    sh "${awsCliPath} s3 cp . s3://katsko-bucket/ --recursive --region eu-north-1"
                }
            }
        }
    }
}

