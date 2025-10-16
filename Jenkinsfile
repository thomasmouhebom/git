pipeline {
    agent any

    environment {
        // Assure-toi que Docker et Ansible sont dans le PATH
        PATH = "/usr/local/bin:/usr/bin:/bin:${env.PATH}"
        ANSIBLE_PLAYBOOK = 'ansible/playbook.yml'
    }

    stages {

        stage('Checkout GitHub via SSH') {
            steps {
                // Cloner le dépôt via SSH
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
