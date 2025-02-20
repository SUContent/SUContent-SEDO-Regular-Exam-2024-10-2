pipeline {
    agent any
    
    environment {
        DOTNET_VERSION = '6.0.x'
    }
    
    stages {
      
        stage('Restore Dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }
        
        stage('Build App') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }
        
        stage('Run All Tests') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
