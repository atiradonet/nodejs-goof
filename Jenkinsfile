pipeline {
  agent any
  stages {
    stage('Snyk Open Source Test') {
      steps {
        // Run Snyk test and fail build on high severity issues
        snykInstallation: snyk@latest
        snykTokenId: snyk-token
        failOnIssues: true
        failOnError: true
      }
    }
  }
}
