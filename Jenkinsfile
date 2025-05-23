pipeline {
    agent any

    environment {
        SNYK_TOKEN = credentials('snyk-token')
    }

    stages {
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Snyk Test') {
            steps {
                sh 'npm install -g snyk'
                sh 'snyk auth $SNYK_TOKEN'
                sh 'snyk test'
            }
        }
    }

    post {
        always {
            echo 'Pipeline complete.'
        }
    }
}
