pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/yourusername/your-repo.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('yourusername/yourimage:latest')
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') {
                        docker.image('yourusername/yourimage:latest').push()
                    }
                }
            }
        }
        stage('Deploy with Ansible') {
            steps {
                ansiblePlaybook playbook: 'deploy.yml', inventory: 'hosts'
            }
        }
    }
}
