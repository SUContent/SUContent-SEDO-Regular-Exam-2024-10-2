pipeline {
    agent any

    stages {
        stage('Restore Dependencies') {
            steps {
                bat '~/.dotnet/dotnet restore'
            }
        }

        stage('Build') {
            steps {
                bat '~/.dotnet/dotnet build --no-restore'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
