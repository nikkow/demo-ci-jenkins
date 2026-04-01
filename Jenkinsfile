pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Récupération du code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Build du projet'
                sh '''
                    mkdir -p dist
                    echo "Version construite le $(date)" > dist/index.html
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Test simple'
                sh '''
                    test -f dist/index.html
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Déploiement simulé'
                sh '''
                    mkdir -p /tmp/deploy-demo
                    cp dist/index.html /tmp/deploy-demo/index.html
                    echo "Déploiement simulé terminé dans /tmp/deploy-demo"
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline terminée avec succès'
        }
        failure {
            echo 'Pipeline en échec'
        }
        always {
            echo 'Fin de la pipeline'
        }
    }
}