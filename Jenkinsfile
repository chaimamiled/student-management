pipeline {
    agent any

    environment {
        APP_NAME = "student-management"
    }

    triggers {
        // Déclenche le pipeline à chaque push Git si configuré avec webhook
        pollSCM('* * * * *') // Vérifier chaque minute (peut être remplacé par webhook)
    }

    stages {
        stage('Hello World') {
            steps {
                echo '👋 Hello World'
                sh 'date'
            }
        }

        stage('Checkout Git') {
            steps {
                echo '📥 Récupération du code source depuis Git'
                git branch: 'main', url: 'https://github.com/chaimamiled/student-management.git'
            }
        }

        stage('Clean') {
            steps {
                echo '🧹 Nettoyage du dossier target'
                sh 'rm -rf target/*'
            }
        }

        stage('Build') {
            steps {
                echo '🔨 Compilation et création du livrable'
                sh 'mvn clean package -DskipTests=true'
            }
        }

        stage('Test') {
            steps {
                echo '✅ Exécution des tests unitaires'
                sh 'mvn test'
            }
        }

        stage('Staging') {
            steps {
                echo '🚀 Déploiement staging (simulation)'
                sh "mkdir -p /tmp/staging && cp target/${APP_NAME}-*.jar /tmp/staging/"
            }
        }

        stage('Browser Testing') {
            parallel {
                stage('Firefox') {
                    steps {
                        echo '🦊 Tests sur Firefox (simulation)'
                        sh 'echo "Tests Selenium sur Firefox"'
                    }
                }
                stage('Edge') {
                    steps {
                        echo '🌐 Tests sur Edge (simulation)'
                        sh 'echo "Tests Selenium sur Edge"'
                    }
                }
            }
        }
    }

    post {
        success { echo '🎉 Pipeline terminé avec succès ✅' }
        failure { echo '❌ Pipeline échoué ❌' }
    }
}
