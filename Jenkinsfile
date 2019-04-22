pipeline {
  agent any
  
  stages {
    stage('Copying playbook') {
      steps {
        sh ' scp ./apache-tomcat.yml root@192.168.0.119:/etc/ansible'
        }
      }
    stage('Ansible syntax check') {
      steps {
        sh 'ssh root@192.168.0.119 "ansible-playbook apache-tomcat.yml --syntax-check"'
        }
      }
    }  
 }
