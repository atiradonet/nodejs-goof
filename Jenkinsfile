pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/atiradonet/nodejs-goof.git', branch: 'main'
      }
    }
    stage('Snyk Open Source Test') {
      steps {
        // Run Snyk test and fail build on high severity issues
        snykInstallation: snyk-app
        snykTokenId: snyk-token
        failOnIssues: true
        failOnError: true
      }
    }
  }
}
