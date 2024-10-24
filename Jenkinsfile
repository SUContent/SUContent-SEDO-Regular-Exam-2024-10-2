pipeline {
    agent any 

  stages {
    
    stage('Restore Dependencies') {
           when {
                branch 'feature-ci-pipeline'
            }
     steps {
          bat 'dotnet restore'
            }
        }
    stage('Dotnet Build') { 
     steps {
          bat 'dotnet build --no-restore' 
            }
        }
    stage('Ececute Tests') { 
        steps {
          bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
