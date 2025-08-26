pipeline {
  agent any
  stages {
    stage('Test') {
      steps {
        echo 'Snyk Security Testing'
        snykSecurity(
          snykInstallation: 'snyk-app',
          snykTokenId: 'snyk-token',
          failOnIssues: true,
          severity: 'high'
        )
      }
    }
  }
}
