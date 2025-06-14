pipeline {
    agent any

    parameters {
        string(name: 'tomcat_dev', defaultValue: '3.90.183.199', description: 'Staging Server')
    }

    triggers {
        pollSCM('* * * * *')
    }

    stages{
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
        stage('Deployments') {
                parallel{
                    stage ('Deploy to Staging'){
                        steps {
                            sh "scp -i /home/linux-user/Projects/Java/Jenkins/tomcat-demo.pem **/target/*.war ec2-user@${params.tomcat_dev}:/opt/tomcat/webapps"
                        }
                    }
                }
            }
    }
}