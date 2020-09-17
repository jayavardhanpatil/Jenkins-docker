pipeline {
	agent any
	environment {
		docketHome = tool 'mydocker'
		mavenHome = tool 'myMaven'
		PATH = "$docketHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout'){
			steps{
				echo "Build"
				echo "PATH - $PATH"
				sh 'mvn --version'
				sh 'docker version'
			}
		}
		stage('Compile'){
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
				sh "mvn test"
			}
		}
		stage('Integration Test'){
			steps{
				sh "mvn failsafe:integration-test failsafe:verify" 
			}
		}
	} 
	post {
		always {
			echo "Finished"
		}
		success {
			echo "Job Success"
		}
		failure {
			echo "Job Failed"
		}
	}
}