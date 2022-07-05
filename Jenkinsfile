node {
  stage('SCM') {
    git 'https://bitbucket.org/souvikgh05/notejam-mysql.git'
  }
  stage('SonarQube analysis') {
    def scannerHome = tool 'SonarScanner 4.6.2';
    withSonarQubeEnv('My SonarQube Server') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}