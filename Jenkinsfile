pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/thomasmouhebom/git.git'
            }
        }

        stage('Deploy with Ansible') {
            steps {
                sh 'ansible-playbook ansible/playbook.yml'
            }
        }
    }

    post {
        success {
            echo '✅ Déploiement réussi ! Accède à http://localhost:8080'
        }
        failure {
            echo '❌ Erreur dans le pipeline'
        }
    }
}

