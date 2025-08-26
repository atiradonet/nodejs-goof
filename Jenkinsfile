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
        withEnv(["SNYK_TOKEN=${env.SNYK_TOKEN}"]) {
          sh 'npx snyk test --severity-threshold=high'
        }
      }
    }
  }
}
