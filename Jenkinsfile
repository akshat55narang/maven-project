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
                 build job: 'deploy-to-prod'
             }
         }
        }
    }
