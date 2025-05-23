pipeline {
    agent any

    environment {
        SNYK_TOKEN = credentials('snyk-token') // Replace with your actual Jenkins credential ID
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install --legacy-peer-deps'
            }
        }

        stage('Snyk Test') {
            steps {
                sh 'npm install -g snyk'
                sh 'snyk test --all-projects --severity-threshold=high'
            }
        }
    }

    post {
        always {
            echo 'Pipeline complete.'
        }
    }
}
