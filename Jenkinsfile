pipeline {
    agent any

    environment {
        S3_BUCKET = 'my-static-site-2025-devops '  // change this
        AWS_DEFAULT_REGION = 'us-west-2' // or your actual region
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ghatak7/aws-cloud-infra-project.git'
            }
        }

        stage('Upload to S3') {
            steps {
                sh 'aws s3 cp index.html s3://$S3_BUCKET/index.html'
            }
        }
    }
}

