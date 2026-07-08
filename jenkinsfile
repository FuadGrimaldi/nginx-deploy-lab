pipeline {
    agent any
    stages {
        stage('Test Connection') {
            steps {
                sh 'ansible target-vm -i inventory_jenkins.yml -m ping'
            }
        }
        stage('Deploy') {
            steps {
                sh 'ansible-playbook site.yml -i inventory_jenkins.yml'
            }
        }
    }
}