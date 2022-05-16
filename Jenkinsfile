pipeline {
  agent any
  stages {
    stage('Scan') {
      steps {
        withSonarQubeEnv(installationName: 'sq1') { 
          sh './mvnw clean org.sonarsource.scanner.maven:sonar-maven-plugin:3.9.0.2155:sonar'
        }
      }
    }
  }
  post {
    success {
        echo 'La comprobación ha sido correcta'
    }
    failure {
        echo 'La comprobación ha fallado'
    }
    unstable {
        echo 'Inestable'
    }
    changed {
        echo 'This will run only if the state of the Pipeline has changed'
        echo 'For example, if the Pipeline was previously failing but is now successful'
    }
    }
}
}

