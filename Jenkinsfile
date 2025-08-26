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
    stage('Deploy and Run with Docker Compose') {
      steps {
        // Remove previous code and clone latest
        sh 'rm -rf /Projects/nodejs-goof && git clone https://github.com/atiradonet/nodejs-goof.git /Projects/nodejs-goof'
        // Run Docker Compose from the project directory
        dir('/Projects/nodejs-goof') {
          //sh 'docker-compose pull'
          //sh 'docker-compose up --build -d'
          //sh 'docker image prune -f'
        }
      }
    }
  }
}
