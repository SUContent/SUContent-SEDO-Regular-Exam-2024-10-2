pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'dotnet restore'
                bat 'dotnet build --configuration Release'
            }
        }
        stage('Test') {
          steps{
              bat 'dotnet test --filter "Category=Unit"' 
          }
        }
    }
    triggers {
        githubPush {
            branch('*/feature-ci-pipeline') 
        }
    }
}