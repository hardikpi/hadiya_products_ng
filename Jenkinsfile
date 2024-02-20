pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                // Add build steps here
                // For example, npm install and npm run build for a Node.js project
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Deploy to S3'){
        steps {
            script {
                sh 'aws s3 sync dist/hadiya_products_admin/ s3://newhadiyabuck'
                sh 'aws cloudfront create-invalidation --distribution-id E2KBXQE7ZXNHR1 --paths "/*"'
            }
        }
    }
    }
}
