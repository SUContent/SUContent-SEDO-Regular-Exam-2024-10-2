pipeline {
    agent any 
    stages {
        stage('Restore Dependencies') { 
            steps {
                bat 'dotnet restore' 
            }
        }
        stage('Dotnet build') { 
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
