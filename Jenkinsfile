pipeline {
    agent any

    stages {
        stage('Restore dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }
        stage('Build app') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }
        stage('Execute all tests') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
