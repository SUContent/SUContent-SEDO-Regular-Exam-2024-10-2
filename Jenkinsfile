pipeline {
    agent any

    environment {
        DOTNET_VERSION = '6.0.x'
    }

    stages {
        stage('Checkout Repository') {
            steps {
                checkout scm
            }
        }

        stage('Setup .NET') {
            steps {
                bat """
                echo Checking if .NET 6.0 is installed...
                dotnet --list-runtimes | findstr "6.0" || (
                    echo .NET 6.0 not found, installing...
                    curl -L https://dot.net/v1/dotnet-install.ps1 -o dotnet-install.ps1
                    powershell -ExecutionPolicy Bypass -File dotnet-install.ps1 -Version 6.0
                    setx PATH "%PATH%;C:\\Program Files\\dotnet"
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
                bat """
                echo Running .NET tests...
                dotnet test --no-build --verbosity normal --logger "trx;LogFileName=TestResults.trx" --results-directory TestResults/
                """
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'TestResults/**/*.trx', fingerprint: true
        }
        failure {
            echo "Build failed! Check test results for details."
        }
    }
}
