pipeline {
    agent any

    stages {        
        stage('Build') {
            when {
    branch 'feature-ci-pipeline'
}
            steps {
                bat 'dotnet build'
            }
        }
        stage('Test') {
            steps {
                bat 'dotnet test'
            }
        }
        
    }
}
