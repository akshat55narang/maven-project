pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
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
        }
    }
}