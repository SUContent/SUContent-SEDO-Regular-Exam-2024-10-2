pipeline {
    agent any

    stages {        
        stage('Build') {
            when {
    branch 'feature-ci-pipeline'
}
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
