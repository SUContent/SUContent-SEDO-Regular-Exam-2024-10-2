pipeline {
    agent any 
    stages {
        stage('Restore dependencies') { 
            steps {
                sh 'dotnet restore'
            }
        }
        stage('Dotnet Build') { 
            steps {
                sh 'dotnet build --no-restore'
            }
        }
        stage('Execute tests') { 
            steps {
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
