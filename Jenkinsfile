pipeline {
  agent any

  stages {

    stage('Restore application dependencies') {
      steps {
        sh 'dotnet restore'
      }
    }

    stage('Build the application') {
      steps {
        sh 'dotnet build --no-restore'
      }
    }

    stage('Run application tests') {
      steps {
        sh 'dotnet test --no-build --verbosity normal'
      }
    }
  }
}
