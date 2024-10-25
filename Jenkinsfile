pipeline{
  agent any

  when{
    branch 'feature-ci-pipeline'
  }

  stages{
     stage('Restore dependencies'){
       steps{
         bat 'dotnet restore'
       }
     }
    stage('Dotnet Build'){
          steps{
            bat 'dotnet build --no-restore'
          }
     }
    stage('Execute tests'){
      steps{
        bat 'dotnet test'
      }
    }
  }
}
