// Old Scripted Syntax
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Integration Test') {
// 		echo "Test"
// 	}
// }

// Declarative Pipeline
pipeline {
	// agent any
	// docker image as an agent
	agent {
		docker {
			image 'maven:3.6.3'
		}
	}

	stages {
		stage('Build') {
			steps {
				sh "mvn --version"
				echo "Build"
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('Integration test') {
			steps {
				echo "Integration Test"
			}
		}
	} 

	// executes after the stages ran. Helps to clean ups
	post {
		always {
			echo "I run always"
		}
		success {
			echo "I run when successful"
		}
		failure {
			echo "I run when fails"
		}
		// changed: executed when the status of a build changes. i.e. from success to failure
	}
}

