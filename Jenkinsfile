pipeline {
	agent any
	tools {
        maven 'localMaven'
    }
	stages{
		stage('Build'){
			steps {
				bat 'mvn clean package'
			}
			post {
				success {
					echo 'Now Archiving...'
					archiveArtifacts artifacts: '**/target/*.war'
				}
			}
		}
		stage('Deploy to staging'){
			steps{
				build job: 'Deploy-to-staging2'
			}
		}
	}
}