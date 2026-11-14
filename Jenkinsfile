pipeline {
    agent any


    environment {
    	PATH = '/opt/maven/bin:$PATH'
    }

    stages {

        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'mvn clean deploy'
		echo '---build completeed---'
            }
        }

        stage('SonarQube Analysis') {
           environment {
		scannerHome = tool 'sonar-qube-scanner'
	   } 
	   steps {
                
                   withSonarQubeEnv("apple-sonarqube-server") {
                        sh "${ScannerHome}/bin/sonar-scanner"
                    }
                
            }
        }
    }
}
