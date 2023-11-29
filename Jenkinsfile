pipeline{
	agent any

	environment {
		scannerHome = tool 'sqrscanner'
	}
	stages {
       		stage('Build') {
            		steps {
				script {
					def sourceDir = 'test'
					def outputDir = 'build'

					sh "mkdir -p ${outputDir}"
                			sh 'javac -d ${outputDir} ${sourceDir}/test.java'
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
