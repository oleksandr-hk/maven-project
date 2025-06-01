pipeline {
    agent any
    tools {
            maven 'localMaven'
        }
    stages {
         stage('Debug') {
                    steps {
                        sh 'env && which mvn && mvn -v'
                    }
         }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}
