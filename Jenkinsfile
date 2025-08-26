pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/atiradonet/nodejs-goof.git', branch: 'main'
      }
    }
    stage('Test') {
      steps {
        echo 'Snyk Security Testing'
        snykSecurity(
          snykInstallation: 'snyk-app',
          snykTokenId: 'snyk-token',
          // place other parameters here
        )
      }
    }
  }
}
