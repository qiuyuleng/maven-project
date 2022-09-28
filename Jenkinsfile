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
    }
}
