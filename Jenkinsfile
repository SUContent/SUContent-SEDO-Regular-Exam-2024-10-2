pipeline {
  agent any

  stages {
    stage('Restore dependencies') {
      when {
        expression {
          return env.BRANCH_NAME == 'feature-ci-pipeline'
        }
      }
      steps {
        bat 'dotnet restore'
      }
    }
    stage('Build project') {
      when {
        expression {
          return env.BRANCH_NAME == 'feature-ci-pipeline'
        }
      }
      steps {
        bat 'dotnet build --no-restore'
      }
    }
    stage('Execute tests') {
      when {
        expression {
          return env.BRANCH_NAME == 'feature-ci-pipeline'
        }
      }
      steps {
        bat 'dotnet test --no-build --verbosity normal'
      }
    }
  }
}
