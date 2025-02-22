pipeline {
    agent any

    stages {  // Missing 'stages' block added
        stage('Restore Dependencies') {
            steps {
                sh 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build --configuration Release --no-restore'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'dotnet test --no-restore --verbosity normal'
            }
        }
    }
}
