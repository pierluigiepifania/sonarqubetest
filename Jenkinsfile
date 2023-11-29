pipeline{
	agent any

	environment {
		scannerHome = tool 'sqrscanner'
	}
	stages {
       		stage('Build') {
            		steps {
                		sh 'javac BubbleSort.java'
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
