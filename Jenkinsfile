pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git 'https://github.com/mubeen456/SIT223-SIT753.git'
            }
        }
        stage('Build') {
            steps {
                // Build code using Maven
                echo "Building..."
            }
            post{
                always{
                    mail to: "mubeenmuhammad098@gmail.com"
                    subject:"Build status Email"
                    body:"Build log attached!"
                }
            }
        }
        stage('Test') {
            steps {
                // Run tests
                echo "Test..."
            }
        }
        stage('Deploy') {
            steps {
                // Deploy code (example: to AWS EC2)
                echo "Deployee..."
            }
        }
    }
    
    post {
        success {
            // Send email notification on success
            emailext(
                to: 'mubeenmuhammad098@gmail.com',
                subject: "Pipeline Success - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The pipeline ${env.JOB_NAME} #${env.BUILD_NUMBER} completed successfully."
            )
        }
        failure {
            // Send email notification on failure
            emailext(
                to: 'mubeenmuhammad098@gmail.com',
                subject: "Pipeline Failure - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The pipeline ${env.JOB_NAME} #${env.BUILD_NUMBER} failed. Please check the logs for details.",
                attachLog: true
            )
        }
    }
}
