pipeline {
    agent any

    stages {
        stage('Build') {
                steps {
                    sh 'mvn clean package'
                }
                post {
                    success {
                        echo 'Archiving Now !'
                        archiveArtifacts artifacts: '**/target/*.war'
                    }

                }
            }
         stage('Deploy to Staging'){
             steps{
                 build job: 'deploy-to-staging'
             }
         }
		stage('Deploy to Production'){
             steps{
             	timeout(time:5, unit:'DAYS'){
             	    input message 'Approve Deployment ?'
             	}

                 build job: 'deploy-to-prod'
             }
             post{
                 success{
                     echo 'Deployed successfully !'
                 }
				failure{
				    echo 'Deployment Failed!! '
				}

             }

         }
        }
    }
