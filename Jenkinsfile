pipeline {
    agent {
        docker {
            image 'node:18' // Includes Node.js and npm
        }
    }

    environment {
        SNYK_TOKEN = credentials('snyk-token') //  Must match the Jenkins credential ID
    }

    stages {
        stage('Install') {
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
