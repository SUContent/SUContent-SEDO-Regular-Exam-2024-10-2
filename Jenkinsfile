pipeline {
    agent any 
    stages {
        stage('Restore dependencies') { 
            steps {
                bat 'dotnet restore'
            }
        }
        stage('Project build') { 
            steps {
                bat 'dotnet build --no-restore' 
            }
        }
        stage('Runs tests') { 
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
