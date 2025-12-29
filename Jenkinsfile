pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/nikhilchavan31/gitaction.git'
            }
        }

        stage('Verify Files') {
            steps {
                sh '''
                echo "Current directory:"
                pwd
                echo "Files:"
                ls -l
                '''
            }
        }

        stage('Run Ansible LEMP Playbook') {
            steps {
                sh '''
                ansible-playbook -i hosts.ini lemp.yml --become
                '''
            }
        }
    }

    post {
        success {
            echo 'LEMP installed successfully using Ansible 🚀'
        }
        failure {
            echo 'Build failed ❌ Check logs'
        }
    }
}
