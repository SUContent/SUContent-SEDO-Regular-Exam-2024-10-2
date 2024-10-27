pipeline {
    agent any

    stages {
        stage('Install dependencies') {
            when {
                branch 'feature-ci-pipeline'
            }
            steps {
                bat 'dotnet restore'
            }
        }
        stage('Set up .NET') {
            when {
                branch 'feature-ci-pipeline'
            }
            steps {
                bat 'dotnet build --no-restore'
            }
        }
        stage('Run Unit Tests') {
            when {
                branch 'feature-ci-pipeline'
            }
            steps {
                bat 'dotnet test Homies.UnitTests/Homies.UnitTests.csproj --no-build --verbosity normal'
            }
        }
        stage('Run Integration Tests') {
            when {
                branch 'feature-ci-pipeline'
            }
            steps {
                bat 'dotnet test Homes.IntegrationTests/Homes.IntegrationTests.csproj --no-build --verbosity normal'
            }
        }
    }
}
