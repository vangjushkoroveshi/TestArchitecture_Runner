pipeline{
	agent any
	stages{
		stage("Start Grid"){
			steps{
				sh "docker-compose -f docker-compose.yaml up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				sh "docker-compose up ui-module api-module db-module"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh "docker-compose -f docker-compose.yml down"
		}
	}
}