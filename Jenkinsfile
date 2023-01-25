pipeline {
    agent { label 'slaveNode1' }
    environment{
        TOKEN = credentials("BOT_TOKEN")
        CHAT_ID = credentials("CHAT_ID")
    }
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
    post {
         success { 
            sh  ("""
                curl -s -X POST https://api.telegram.org/bot${TOKEN}/sendMessage -d chat_id=${CHAT_ID} -d parse_mode=markdown -d text='*Project name*: task9_jenkins \n *Branch*: [$GIT_BRANCH](https://github.com/yurakorabel/task9_jenkins) \n *Build* : [OK](${BUILD_URL}consoleFull)'
            """)
         }

         aborted {
            sh  ("""
                curl -s -X POST https://api.telegram.org/bot${TOKEN}/sendMessage -d chat_id=${CHAT_ID} -d parse_mode=markdown -d text='*Project name*: task9_jenkins \n*Branch*: [$GIT_BRANCH](https://github.com/yurakorabel/task9_jenkins) \n*Build* : [Aborted](${BUILD_URL}consoleFull)'
            """)
         }
         failure {
            sh  ("""
                curl -s -X POST https://api.telegram.org/bot${TOKEN}/sendMessage -d chat_id=${CHAT_ID} -d parse_mode=markdown -d text='*Project name*: task9_jenkins \n*Branch*: [$GIT_BRANCH](https://github.com/yurakorabel/task9_jenkins) \n*Build* : [Not OK](${BUILD_URL}consoleFull)'
            """)
         }

    }
}
