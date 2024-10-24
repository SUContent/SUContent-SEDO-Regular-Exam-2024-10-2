pipeline{
  agent any
  
  stages {
      stage('Restore dependencies') {
        when {
          branch 'feature-ci-pipeline'
        }
        steps {
          bat 'dotnet restore'
        }
      }
      stage('Dotnet build') {
        when {
          branch 'feature-ci-pipeline'
        }
        steps {
          bat 'dotnet build --configuration Release'
        }
      }
      stage('Execute tests') {
        when {
          branch 'feature-ci-pipeline'
        }
        steps {
          bat 'dotnet test --configuration Release --no-build --verbosity normal'
        }
      }
  }
}
