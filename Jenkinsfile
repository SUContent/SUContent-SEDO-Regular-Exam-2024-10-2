pipeline {
  agent any

  stages {
    stage('Restore dependencies') {
      when {
        branch 'origin/feature-ci-pipeline'
      }
      steps {
        bat 'dotnet restore'
      }
    }
    stage('Build project') {
      when {
        branch 'origin/feature-ci-pipeline'
      }
      steps {
        bat 'dotnet build --no-restore'
      }
    }
    stage('Execute tests') {
      when {
        branch 'origin/feature-ci-pipeline'
      }
      steps {
        bat 'dotnet test --no-build --verbosity normal'
      }
    }
  }
}
