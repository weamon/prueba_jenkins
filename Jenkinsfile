pipeline {
  agent any
  stages {
    stage ('SonarQube analysis') {
      steps {
        withSonarQubeEnv('sq1') {
          sh "/sonar-scanner/bin/sonar-scanner -Dsonar.projectKey=develop -Dsonar.sources=."
        }        
      }
    }
    stage ("Quality Gate") {
      steps {
        timeout(time: 2, unit: 'MINUTES') {
          waitForQualityGate abortPipeline: true
        }
      }
    }
  }
}
