pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

      stage('Restore dependancies') {
            steps {
                bat 'dotnet restore'
            }
        }
      
        stage('Build') {
            steps {
                bat 'dotnet build --configuration Release'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'dotnet test --configuration Release'
            }
        }
    }

    post {
        always {
            echo "Pipeline complete!"
        }
    }
}
