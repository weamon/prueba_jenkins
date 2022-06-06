pipeline {
  agent any
  stages {
    stage ('SonarQube analysis') {
      steps {
        withSonarQubeEnv('sq1') {
          sh "/sonar-scanner-4.7.0.2747-linux/bin/sonar-scanner -Dsonar.projectKey=prueba_bootstrap -Dsonar.sources=./web"
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
    /*stage ("Copiando los archivos") {
      steps {
        sh "scp -i ~/.ssh/claveCli /var/jenkins_home/workspace/try/web/* ivan@10.0.2.15:/home/ivan/Escritorio/deploy"
      }
    }*/
  }
}
