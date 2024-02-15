pipeline {
    agent any

    environment {
        // Define environment variables for GCP credentials
        GOOGLE_CREDENTIALS = credentials('devsecops-414405')
        GOOGLE_PROJECT = 'devsecops-414405'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout source code from your version control system (e.g., Git)
                checkout scm
            }
        }

        stage('Terraform Init') {
            steps {
                // Execute Terraform init to initialize the working directory
                script {
                    sh 'terraform init'
                }
            }
        }

        stage('Terraform Plan') {
            steps {
                // Execute Terraform plan to generate an execution plan
                script {
                    sh 'terraform plan -var project="${GOOGLE_PROJECT}"'
                }
            }
        }

        stage('Terraform Apply') {
            steps {
                // Execute Terraform apply to apply the changes
                script {
                    sh 'terraform apply -auto-approve -var project="${GOOGLE_PROJECT}"'
                }
            }
        }

        stage('Terraform Destroy') {
            steps {
                // Execute Terraform destroy to destroy the infrastructure
                script {
                    sh 'terraform destroy -auto-approve -var project="${GOOGLE_PROJECT}"'
                }
            }
        }
    }
}
