pipeline {
    agent any
    parameters {
        string(name: 'VM_NAME', description: 'Enter the IP or FQDN of remote windows machine'),
        string(name: 'USERNAME', description: 'Enter username to connect to windows machine'),
        password:(name: 'PASSWORD', description: 'Enter password to connect to windows machine')
    }
    stages {
        stage('Run playbook to install package on remote windows VM') {
            steps {
                sh "ansible-playbook -i ${VM_NAME}, -e "ansible_user=${USERNAME}" -e "ansible_password=${PASSWORD}" -e "ansible_connection=winrm" -e "ansible_winrm_transport=basic" -e "ansible_port=5985" windows_updater.yml"
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}

// Note: On windows machine, winrm should be configured for the user account which we tend to use
