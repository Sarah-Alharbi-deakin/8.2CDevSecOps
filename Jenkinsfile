pipeline {
  agent any
  environment {
    SNYK_TOKEN = credentials('snyk-token')  // ✅ Secure access
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
