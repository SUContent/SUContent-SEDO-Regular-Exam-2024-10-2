pipeline {
    agent any 
  
    stages {
        stage('Restore dependencies') { 
            steps {
                sh 'dotnet restore'
            }
        }
      
        stage('Build the application') { 
            steps {
                sh 'dotnet build --no-restore'
            }
        }
      
        stage('Test the application') { 
            steps {
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
