pipeline {
    agent any
    tools {
        maven 'localMaven'
    }
    pipeline {
        agent any
        stages{
            stage('Build') {
                steps{
                    sh 'mvn clean package'
                }
            }
        }
    }
}