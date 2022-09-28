pipeline {
    agent any
    tools{
        maven 'local maven'
    }
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Start to store...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to staging'){
            steps{
                build job:'deploy-to-staging'
            }
        }
        stage ('Deploy to Production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'If deploy to production?'
                }

                build job: 'deploy-to-production'
            }
            post {
                success {
                    echo 'Success deploy to production'
                }

                failure {
                    echo 'Deploy failure'
                }
            }
        }

    }
}
