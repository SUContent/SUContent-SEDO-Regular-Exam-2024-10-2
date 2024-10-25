pipeline {
    agent any
    stages {
        stage('Restore Dependencies') {
            steps {
                // Restore dependencies
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                // Build the application without restoring dependencies again
                bat 'dotnet build --no-restore'
            }
        }

        stage('Test') {
            steps {
                // Run tests with normal verbosity
               bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
