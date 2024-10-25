pipeline{
  agent any

  stages{
      when{
    branch 'feature-ci-pipeline'
  }
     stage('Restore dependencies'){
       steps{
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
