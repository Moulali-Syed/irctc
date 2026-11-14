pipeline {
    agent any


    environment {
    	"PATH+MAVEN" = '/opt/maven/bin'
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
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                
            }
        }
    }
}
