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
                bat 'dotnet test --filter "Category=Unit"' 
            }
        }
    }
    post {
        always {
            archiveArtifacts '**/*.trx' 
        }
    }
  
    triggers { 
        githubPush()
    }
}