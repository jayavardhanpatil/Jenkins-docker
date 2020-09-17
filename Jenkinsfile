pipeline {
	agent any
	environment {
		docketHome = tool 'mydocker'
		mavenHome = tool 'myMaven'
		PATH = "$docketHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('build'){
			steps{
				echo "Build"
				echo "PATH - $PATH"
				sh 'mvn --version'
				sh 'docker version'
			}
		}
		stage('Test'){
			steps{
				echo "Test"
			}
		}
		stage('Integration Test'){
			steps{
				echo "Integration Test"
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