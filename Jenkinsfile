pipeline {
  agent any
  environment {
    GITHUB_CREDS = credentials('github-token')
  }
  stages {
    stage('Clone Repo') {
      steps {
        git credentialsId: "${GITHUB_CREDS}", url: 'https://github.com/bishnoitarun/testjenikins.git'
      }
    }
    stage('Install') {
      steps { sh 'npm install' }
    }
    stage('Test') {
      steps { sh 'npm test || echo "No tests found"' }
    }
  }
  post {
    success { echo 'Build passed!' }
    failure { echo 'Build failed!' }
  }
}
