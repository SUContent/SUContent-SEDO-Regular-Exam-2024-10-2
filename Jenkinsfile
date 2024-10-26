pipeline {
    agent any
    stages {
        stage('Run on feature-ci-pipeline branch') {
            when {
                branch 'feature-ci-pipeline'
            }
            stage('Restore Dependencies') {
                steps {
                    bat 'dotnet restore'
                }
            }
            stage('Dotnet Build') {
                steps {
                    bat 'dotnet build --no-restore'
                }
            }
            stage('Execute Tests') {
                steps {
                    bat 'dotnet test --no-build --verbosity normal'
                }
            }
        }
    }
}
