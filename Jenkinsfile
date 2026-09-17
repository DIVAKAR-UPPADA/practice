pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps { checkout scm }
    }
    stage('Deploy with Ansible') {
      steps {
        sh 'ansible-playbook -i ansible/inventory.ini ansible/deploy.yml'
      }
    }
    stage('Verify') {
      steps {
        sh 'curl --fail --retry 12 --retry-delay 5 http://172.31.46.101:5000/'
      }
    }
  }
}
