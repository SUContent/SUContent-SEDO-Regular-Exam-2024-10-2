pipeline {
    agent any 

    stages {
        stage('Restore dependencies') { 
            when {
                branch: "feature-ci-pipeline"
            }
            steps {
                sh 'dotnet restore'
            }
        }
      
        stage('Build the application') { 
            when {
                branch: "feature-ci-pipeline"
            }
            steps {
                sh 'dotnet build --no-restore'
            }
        }
      
        stage('Test the application') { 
            when {
                branch: "feature-ci-pipeline"
            }
            steps {
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
