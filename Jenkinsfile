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
                scannerHome = tool 'SonarQubeScanner'
            }
            steps {
                withSonarQubeEnv('souvik05bit') {
                    sh '''
                    ${scannerHome}/bin/sonar-scanner \
                    -Dsonar.organization=souvikgh05 \
                    -Dsonar.projectKey=jenkins-project \
                    -Dsonar.java.binaries=build/classes/java/ \
                    -Dsonar.python.version=3
                    '''

                }
            }
        }
    }
}