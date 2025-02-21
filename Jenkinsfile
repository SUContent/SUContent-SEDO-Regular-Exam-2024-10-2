pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                bat 'dotnet restore'
                bat 'dotnet build --configuration Release'
            }
        }
        stage('Test') {
            steps {
                bat 'dotnet test --logger "trx;LogFileName=testresults.trx" --results-directory TestResults'
            }
        }
    }
    post {
        always {
            archiveArtifacts 'TestResults/*.trx'
        }
    }
  
    triggers { 
        githubPush()
    }
}