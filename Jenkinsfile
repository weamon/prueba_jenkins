pipeline {
  agent any
  //node ('SCM') {
  //  git 'https://github.com/weamon/prueba_jenkins.git'
  //}
  stages {
    stage ('SonarQube analysis') {
      steps {
        //def scannerHome = tool 'SonarScanner 4.0';
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
