pipeline {
    agent any
     environment {
        TF_VAR_bucket_name = 'pankaj-terraform-demo-20260813456'
        TF_VAR_aws_region  = 'ap-southeast-2'
    }

    triggers {
        githubPush()
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Check Terraform Files') {
            steps {
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('Terraform Init') {
            steps {
                sh 'terraform init -input=false'
            }
        }

        stage('Terraform Validate') {
            steps {
                sh 'terraform validate'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan -out=tfplan'
            }
        }

        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve tfplan'
            }
        }
    }
}