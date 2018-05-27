pipeline{
    agent any
    stages{
        stage('Build'){
           steps{
       		sh 'mvn clean package'
  			}
         }
        stage('Deploy to Staging'){
            steps{
            	echo 'Archiving Artifacts!'
            	archiveArtifacts artifacts: '**/target/*.war'
            }
			post{
			    success{
			        build job: 'deploy-to-staging'
			    }

			}

		}
    }
}
