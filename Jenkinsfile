pipeline {
    agent any

    environment {
        DOCKER_IMAGE_NAME = 'hello-world' // Nom de l'image Docker
        DOCKER_TAG = 'latest' // Tag de l'image Docker
    }

    stages {
        stage('Cloner le dépôt') {
            steps {
                git 'https://github.com/Beaurain-Hugo/app_pipeline_jenkins' // URL de votre dépôt Git
            }
        }

        stage('Exécuter les tests unitaires') {
            steps {
                script {
                    // Exemple de commande pour exécuter un fichier Python avec des tests unitaires
                    sh 'python3 -m unittest python.py'
                }
            }
        }

        stage('Builder l\'image Docker') {
            steps {
                script {
                    // Construction de l'image Docker
                    sh 'docker build -t ${DOCKER_IMAGE_NAME}:${DOCKER_TAG} .'
                }
            }
        }

        stage('Déployer sur le serveur de test') {
            steps {
                script {
                    // Exemple de déploiement : déployer l'image Docker sur un serveur de test
                    // Vous pouvez adapter cette commande pour déployer l'image sur un serveur de test réel via SSH
                    sh 'docker run -d -p 8080:8080 ${DOCKER_IMAGE_NAME}:${DOCKER_TAG}'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline terminé avec succès!'
        }
        failure {
            echo 'Le pipeline a échoué.'
        }
    }
}

