pipeline {
    agent any

    environment {
        DOTNET_VERSION = '6.0' 
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/dimataa1/SUContent-SEDO-Regular-Exam-2025', branch: 'feature-ci-pipeline'
            }
        }

        stage('Setup .NET') {
            steps {
                script {
                    bat 'dotnet --version'  
                }
            }
        }

        stage('Restore Dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build Application') {
            steps {
                bat 'dotnet build --configuration Release --no-restore'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }


}
