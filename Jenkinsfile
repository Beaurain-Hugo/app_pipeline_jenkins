pipeline {
    agent any

    stages {
        stage('Clôner le dépot') {
            steps {
                // Cloner la branche main du dépôt public
                git url: 'https://github.com/Beaurain-Hugo/app_pipeline_jenkins.git', branch: 'main'
            }
        }
        stage('Vérifier la version de Python') {
            steps {
                script {
                    // Vérifier que python3 et pip3 sont disponibles dans le PATH
                    sh 'python3 --version'
                    sh 'pip3 --version'
                }
            }
        }
        stage('Installer les dépendances') {
            steps {
                script {
                    // Installer les dépendances dans l'environnement global
                    sh 'pip3 install --break-system-packages -r requirements.txt'
                }
            }
        }
        stage('Lancer les Tests') {
            steps {
                script {
                    // Exécuter les tests avec python3
                    sh 'python3 -m unittest discover -s tests'
                }
            }
        }
    }
}
