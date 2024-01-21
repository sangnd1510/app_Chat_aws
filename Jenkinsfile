pipeline {

    agent any
    environment {
        ANSIBLE_HOST_KEY_CHECKING = 'False'
    }
    stages {

        stage('Deploy app to cloud') {
           
            steps {
                withCredentials([file(credentialsId: 'app_chat_key', variable: 'app_chat_key')]) {
                    sh 'ls -la'
                    sh "cp /$app_chat_key app_chat_key"
                    sh 'cat app_chat_key'
                    sh 'ansible --version'
                    sh 'ls -la'
                    sh 'chmod 400 app_chat_key '
                    sh 'ansible-playbook -i hosts --private-key app_chat_key playbook.yml'
            }
            }
        }
        
    }
    post {
        // Clean after build
        always {
            cleanWs()
        }
    }
}