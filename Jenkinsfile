pipeline{
	agent any
	stages{
		stage("Start Grid"){
			steps{
				bat "docker-compose -f docker-compose.yaml --compatibility up -d selenium-hub firefox chrome"
			}
		}
		stage("Run Test"){
			steps{
				bat "docker-compose -f docker-compose.yaml up ui-module api-module db-module"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			bat "docker-compose -f docker-compose.yaml down"
		}
	}
}