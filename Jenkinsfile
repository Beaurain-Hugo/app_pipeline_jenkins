pipeline {
    agent any

    stages {
        stage('Cloner le dépôt') {
            steps {
                git 'https://github.com/Beaurain-Hugo/app_pipeline_jenkins' // URL de votre dépôt Git
            }
        }
        stage('Check Python Version') {
            steps {
                script {
                    // Vérifier que python3 et pip3 sont disponibles dans le PATH
                    sh 'python3 --version'
                    sh 'pip3 --version'
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                script {
                    // Installer les dépendances dans l'environnement global
                    sh 'pip3 install --break-system-packages -r flask==2.2.3'
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    // Exécuter les tests avec python3
                    sh 'python3 -m unittest discover -s tests'
                }
            }
        }
    }
}
