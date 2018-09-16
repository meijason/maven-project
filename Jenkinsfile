pipeline {
    agent any
    
    tools {
        maven 'localMaven'
    }
 
    stages{
        stage('Build'){
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                build job: 'Deploy-to-staging'
            }
        }
    }
}