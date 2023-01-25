pipeline {
    agent { label 'slaveNode1' }
    stages {
        stage('play slave') {
            steps {
                sh '''
                    cd ansible_deploy
                    ansible-playbook playbook_slave.yml
                '''
            }
        }
        stage('play main website') {
            when {
                anyOf {
                    branch "main"
                }
            }
            steps {
                sh '''
                    cd ansible_deploy
                    ansible-playbook playbook_website.yml
                '''
            }
        }
    }
}
