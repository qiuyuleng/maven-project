pipeline {
    agent any
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
    }
}
