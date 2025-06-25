pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *') // Optional: Poll for changes every 5 minutes
    }

    stages {
        stage('Checkout') {
            steps {
                // Clone the repository
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Build the application (adjust this command for your project)
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                // Run all tests (adjust this command for your project)
                sh 'npm test'
            }
        }
    }

    post {
        always {
            // Archive test results or artifacts if needed
            junit 'test-results/*.xml' // Adjust the path to your test results
        }
        success {
            echo 'Build and tests succeeded!'
        }
        failure {
            echo 'Build or tests failed!'
        }
    }
}
