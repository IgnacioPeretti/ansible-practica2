pipeline {
    agent { label 'ansible-controller' }
    environment {
        ANSIBLE_PRIVATE_KEY=credentials('ansible-private-key') 
        ANSIBLE_CONFIG='./actividad/ansible.cfg'
    }
    stages {
        stage('Install Ansible collections'){
            steps {
                sh 'ansible-galaxy collection install -r ./actividad/requirements.yml'
            }
        }
        stage('Run Ansible Playbook from Jenkins') {
            steps {
                sh 'ansible-playbook -i ./inventory.init --private-key=$ANSIBLE_PRIVATE_KEY ./main.yml'
            }
        }
    }
}