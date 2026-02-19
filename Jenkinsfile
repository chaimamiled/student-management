pipeline {
    agent any

    stages {
        stage('Hello World') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Vérifier Maven') {
            steps {
                sh 'mvn -version'
            }
        }
    }
}
