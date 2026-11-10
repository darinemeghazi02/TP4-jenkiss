pipeline {
    agent any

    parameters {
        string(name: 'VERSION', defaultValue: '1.0', description: 'Version à déployer')
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Lancer les tests ?')
    }

    environment {
        APP_NAME = 'tp4-app'
        NEW_VERSION = '1.0.0'
    }

    stages {
        stage('Build') {
            steps {
                echo "Build de ${APP_NAME} version ${params.VERSION}"
            }
        }

        stage('Test') {
            when {
                expression { params.executeTests == true }
            }
            steps {
                echo 'Exécution des tests...'
            }
        }

        stage('Deploy') {
            steps {
                echo "Déploiement de la version ${NEW_VERSION}"
            }
        }
    }

    post {
        always {
            echo 'Pipeline terminé'
        }
        success {
            echo 'Succès'
        }
        failure {
            echo 'Échec'
        }
    }
}
