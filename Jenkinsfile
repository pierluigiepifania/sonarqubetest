pipeline{
	agent any

	environment {
		scannerHome = tool 'sqrscanner'
	}
	stages {
       		stage('Build') {
            		steps {
				script {
					def outputDir = 'build'
                			sh 'javac -d build test/test.java test/prova.java'
				}
            		}
        	}
		stage ('SonarQube Analysis') {
			steps {
				script {
					def scanner = tool 'sqrscanner'
					withSonarQubeEnv ('server-sonarqube-gts') {
						sh "${scannerHome}/bin/sonar-scanner -X"
					}
				}
			}
		}
	}
}
