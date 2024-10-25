pipeline{
  agent any

  stages{
     stage('Restore dependencies'){
       steps{
           when{
    branch 'feature-ci-pipeline'
  }
         bat 'dotnet restore'
       }
     }
    stage('Dotnet Build'){
        when{
    branch 'feature-ci-pipeline'
  }
          steps{
            bat 'dotnet build --no-restore'
          }
     }
    stage('Execute tests'){
        when{
    branch 'feature-ci-pipeline'
  }
      steps{
        bat 'dotnet test'
      }
    }
  }
}
