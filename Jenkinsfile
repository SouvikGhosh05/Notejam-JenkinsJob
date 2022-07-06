pipeline {
    agent any

    stages {
        stage('Cleaning Up WS') {
            steps {
                cleanWs ()
                sh 'git clone https://souvikgh05bit@bitbucket.org/souvikgh05/notejam-mysql.git'
            }
        }
        stage('Sonarqube') {
            environment {
                scannerHome = tool 'SonarQubeScanner-4.6.2'
            }
            steps {
                withSonarQubeEnv('SonarQubeScanner-4.6.2') {
                    sh '''
                    ${scannerHome}/bin/sonar-scanner \
                    -Dsonar.organization=default-organization \
                    -Dsonar.projectKey=jenkins-project \
                    -Dsonar.java.binaries=build/classes/java/ \
                    -Dsonar.python.version=3 \
                    -Dsonar.sourceEncoding=UTF-8
                    '''
                }
            }
        }
    }
}