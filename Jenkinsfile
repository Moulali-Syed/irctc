pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building application...'

                withEnv(["PATH=/opt/maven/bin:${env.PATH}"]) {
                    sh 'mvn clean package'
                }

                echo '---build completed---'
            }
        }

        stage('SonarQube Analysis') {
            environment {
                scannerHome = tool 'sonar-qube-scanner'
            }
            steps {
                withSonarQubeEnv('apple-sonarqube-server') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
