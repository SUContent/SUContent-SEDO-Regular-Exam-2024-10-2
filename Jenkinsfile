pipeline {
    agent any
    stages {
        stage('Restore dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }
        stage('Dotnet Build') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }
        stage('Execute tests') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'develop') {
                        bat 'dotnet test Homies.UnitTests/Homies.UnitTests.csproj --no-build --verbosity normal'
                    } else if (env.BRANCH_NAME == 'staging') {
                        bat 'dotnet test Homes.IntegrationTests/Homes.IntegrationTests.csproj --no-build --verbosity normal'
                    }
                }
            }
        }
    }
}
