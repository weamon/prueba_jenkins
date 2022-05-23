pipeline {
  agent {any}
  node ('SCM') {
    git 'https://github.com/weamon/prueba_jenkins.git'
  }
  stage ('SonarQube analysis') {
    def scannerHome = tool 'SonarScanner 4.0';
    withSonarQubeEnv('sq1')
    sh "/sonar-scanner/bin/sonar-scanner"
  }
}
