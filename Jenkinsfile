pipeline {
    agent any

    environment {
        // Chemin vers ton playbook Ansible
        ANSIBLE_PLAYBOOK = 'ansible/playbook.yml'
    }

    stages {

        stage('Checkout GitHub via SSH') {
            steps {
                // Cloner le dépôt en SSH
                git branch: 'main',
                    url: 'git@github.com:thomasmouhebom/git.git',
                    credentialsId: 'ssh-github-credentials'
            }
        }

        stage('Deploy with Ansible') {
            steps {
                // Lancer le playbook Ansible
                sh "ansible-playbook ${ANSIBLE_PLAYBOOK}"
            }
        }

    }

    post {
        success {
            echo 'Pipeline terminé avec succès ! 🚀'
        }
        failure {
            echo 'Erreur dans le pipeline ❌'
        }
    }
}
