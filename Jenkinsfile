pipeline {
 	agent any
 	stages {
 		stage ('Checkout') {
 			steps {
 				git branch:'master', url: 'https://github.com/Kenrick78/3103practice.git'
 			}
 		}
 
 		stage('Code Quality Check via SonarQube') {
 			steps {
 				script {
 					def scannerHome = tool 'SonarQube';
 						withSonarQubeEnv('SonarQube') {
 						sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=Testing -Dsonar.sources=."
 						}
 					}
 				}
 			}
 		}
 	post {
 		always {
 			recordIssues enabledForFailure: true, tool: sonarQube()
 		}
 	}
}