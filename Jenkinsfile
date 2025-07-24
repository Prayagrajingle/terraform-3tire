pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY_ID = credentials('aws-access-key')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-key')
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Prayagrajingle/terraform-3tire.git
'
            }
        }
        stage('Init Terraform') {
            steps {
                sh 'terraform init'
            }
        }
        stage('Validate') {
            steps {
                sh 'terraform validate'
            }
        }
        stage('Plan') {
            steps {
                sh 'terraform plan -out=tfplan'
            }
        }
        stage('Apply') {
            steps {
                input message: "Apply changes?"
                sh 'terraform apply tfplan'
            }
        }
    }
}
