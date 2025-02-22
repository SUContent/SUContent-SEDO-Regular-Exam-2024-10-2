pipeline {
    agent any

    environment {
        DOTNET_VERSION = '6.0' 
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'feature-ci-pipeline', url: 'https://github.com/dimataa1/SUContent-SEDO-Regular-Exam-2025'
            }
        }

        stage('Setup .NET') {
            steps {
                script {
                    sh 'dotnet --version' 
                }
            }
        }

        stage('Restore Dependencies') {
            steps {
                sh 'dotnet restore'
            }
        }

        stage('Build Application') {
            steps {
                sh 'dotnet build --configuration Release --no-restore'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }

    post {
        always {
            junit '**/TestResults/*.trx' 
        }
    }
}
