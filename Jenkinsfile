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
	agent any
	// docker image as an agent
	// agent {
	// 	docker {
	// 		image 'maven:3.6.3'
	// 	}
	// }

	// docker and maven set up in Jenkins UI
	environment {
		dockerHome = tool 'my-docker'
		mavenHome = tool 'my-maven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages {
		stage('Checkout') {
			steps {
				sh "mvn --version"
				sh "docker version"
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Compile') {
			steps {
				sh "mvn clean compile"
			}
		}
		stage('Test') {
			steps {
				sh "mvn test"
			}
		}
		stage('Integration test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
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

