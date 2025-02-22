pipeline {
    agent any

    stages {
        stage('Checkout Repository') {
            steps {
                checkout scm
            }
        }

        stage('Setup .NET') {
            steps {
                bat """
                echo Installing .NET...
                dotnet --version || (
                    echo .NET not found, installing...
                    curl -L https://dot.net/v1/dotnet-install.ps1 -o dotnet-install.ps1
                    powershell -ExecutionPolicy Bypass -File dotnet-install.ps1 -Version 6.0
                )
                """
            }
        }

        stage('Restore Dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'dotnet test --no-build --verbosity normal --logger trx --results-directory TestResults/'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'TestResults/**/*.trx', fingerprint: true
        }
    }
}
