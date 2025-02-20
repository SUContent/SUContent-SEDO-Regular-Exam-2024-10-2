pipeline {
    agent any

    stages {
        stage('Restore dependencies') {
            when { branch 'feature-ci-pipeline' }  // Тук е поставено правилно
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            when { branch 'feature-ci-pipeline' }
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Run Tests') {
            when { branch 'feature-ci-pipeline' }
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}

