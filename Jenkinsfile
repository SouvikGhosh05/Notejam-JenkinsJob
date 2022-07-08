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
                scannerHome = tool 'SonarQubeScanner-4.7.0'
                SONARCLOUD_TOKEN = credentials('sonarcloud-token')
            }
            steps {
                withSonarQubeEnv('SonarQubeScanner-4.7.0') {
                    sh '''
                    ${scannerHome}/bin/sonar-scanner \
                    -Dsonar.host.url=https://sonarcloud.io/ \
                    -Dsonar.login=$SONARCLOUD_TOKEN \
                    -Dsonar.organization=souvikgh05 \
                    -Dsonar.projectKey=souvikgh05_notejam-mysql \
                    -Dsonar.java.binaries=build/classes/java/ \
                    -Dsonar.python.version=3 \
                    -Dsonar.sourceEncoding=UTF-8 \
                    -Dsonar.verbose=true
                    '''
                }
            }
        }
    }
}
