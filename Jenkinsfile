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
		// stage('Test'){
		// 	steps{
		// 		sh "mvn test"
		// 	}
		// }
		// stage('Integration Test'){
		// 	steps{
		// 		sh "mvn failsafe:integration-test failsafe:verify" 
		// 	}
		// }

		stage('Package'){
			steps{
				sh "mvn package -DskipTests" 
			}
		}

		stage('Build docker Image'){
			steps{
				script {
					dockerImage = docker.build("jayavardhanpatil/first-dev_ops:")
				}
			}
		}

		stage('Push docker Image'){
			steps{
				script {
					docker.wiRegistry('','6f86982d-2a54-4950-a02e-643221ef8364'){
					dockerImage.push();
					dockerImage.push('latest');
				}
			}
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