pipeline {
    agent any
    stages {
        stage('Git Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/ton-utilisateur/ton-repo.git'
            }
        }
        stage('Deploy with Ansible') {
            steps {
                sh 'ansible-playbook ansible/playbook.yml'
            }
        }
    }
}

