pipeline
{
  agent any
  stages{
       stage("Build app"){
            steps{
              bat 'dotnet build --verbosity normal'
            }
       }
    stage("Execute all tests"){
            steps{
              bat 'dotnet test --no-build --verbosity normal'
            }
       }
  }
}
