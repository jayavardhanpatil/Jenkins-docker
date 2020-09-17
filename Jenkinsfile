pipeline {
	agent {
        docker {
            image 'maven:3-alpine'
            //args '-v /root/.m2:/root/.m2'
        }
    }
	stages {
		stage('build'){
			steps{
				echo "Build"
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