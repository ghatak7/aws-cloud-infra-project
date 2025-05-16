pipeline {
    agent any

    environment {
        S3_BUCKET = 'my-static-site-2025-devops'
        AWS_DEFAULT_REGION = 'us-west-2'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ghatak7/aws-cloud-infra-project.git'
            }
        }

        stage('Upload to S3') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'aws-credentials', usernameVariable: 'AWS_ACCESS_KEY_ID', passwordVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                    sh '''
                        aws s3 cp index.html s3://$S3_BUCKET/index.html
                    '''
                }
            }
        }
    }
}

