pipeline {  
    agent any  

    stages {  
        stage('Build') {  
            steps {  
                // Изграждане на проекта.  
                bat "dotnet build --configuration Release"  
            }  
        }  

        stage('Test') {  
            steps {  
                // Извеждане на тестовете.  
                bat "dotnet test --no-build --verbosity normal"  
            }  
        }  
    }  

    post {  
        success {  
            // Ако всичко е успешно, може да добавите допълнителни стъпки.  
            echo 'Build and tests completed successfully!'  
        }  
        failure {  
            // При неуспешно завършване, може да изпратите известие или лог.  
            echo 'Build or tests failed. Please check the logs.'  
        }  
    }  
}
