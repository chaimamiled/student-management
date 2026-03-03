pipeline {
    agent any

    environment {
        SONAR_TOKEN = credentials('squ_696d38fe068dd19f95ced8b8001eb3d575c5c099') // ton token SonarQube
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/chaimamiled/student-management.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                sh "mvn sonar:sonar -Dsonar.host.url=http://192.168.50.4:9000 -Dsonar.login=$SONAR_TOKEN"
            }
        }
    }
}
