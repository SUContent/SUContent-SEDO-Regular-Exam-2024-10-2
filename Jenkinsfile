pipeline {
    agent any

    stages {

        stage('Restore Dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'dotnet test'
            }
        }

    }
}
