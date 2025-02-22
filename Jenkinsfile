pipeline {
    agent any

    environment {
        DOTNET_VERSION = '6.0.x'
        TEST_RESULTS_DIR = 'TestResults/'
    }

    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()  // Ensure a clean Jenkins workspace before running
            }
        }

        stage('Checkout Repository') {
            steps {
                checkout scm
            }
        }

        stage('Setup .NET') {
            steps {
                bat """
                echo Checking if .NET is installed...
                dotnet --version || (
                    echo .NET not found, installing...
                    curl -L https://dot.net/v1/dotnet-install.ps1 -o dotnet-install.ps1
                    powershell -ExecutionPolicy Bypass -File dotnet-install.ps1 -Version ${DOTNET_VERSION}
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

        stage('Start Required Services') {
            steps {
                script {
                    echo "Starting necessary services for testing..."
                }
                bat """
                echo Checking if MSSQLSERVER is running...
                net start MSSQLSERVER || echo MSSQLSERVER is already running
                
                echo Starting API Backend...
                start /b dotnet run --project Homies.Api
                timeout /t 10 /nobreak  // Wait for API to be fully available
                """
            }
        }

        stage('Run Tests') {
            steps {
                bat """
                echo Running .NET tests...
                dotnet test --no-build --verbosity detailed --logger "trx;LogFileName=TestResults.trx" --results-directory ${TEST_RESULTS_DIR}
                """
            }
        }
    }

    post {
        always {
            echo "Archiving test results..."
            archiveArtifacts artifacts: 'TestResults/*.trx', fingerprint: true
        }
        failure {
            echo "Build failed! Check test results for details."
        }
    }
}
