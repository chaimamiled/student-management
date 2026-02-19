pipeline {
    agent any

    stages {
        stage('Hello World') {
            steps {
                echo 'Hello World'
                sh 'date'
            }
        }

        stage('Checkout Git') {
            steps {
                git branch: 'main', url: 'https://github.com/chaimamiled/student-management.git'
            }
        }

        stage('Build Maven') {
            steps {
                sh 'mvn clean package -DskipTests=true'
            }
        }
    }

    post {
        success { echo 'Pipeline terminé avec succès ✅' }
        failure { echo 'Pipeline échoué ❌' }
    }
}
