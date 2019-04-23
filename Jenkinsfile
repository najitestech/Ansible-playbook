def host = '192.168.0.119'
pipeline {
  agent any
  
  stages {
    stage('Copying playbook') {
      steps {
        sh ' scp ./apache-tomcat.yml root@${host}:/etc/ansible'
        }
      }
    stage('Ansible syntax check') {
      steps {
        sh 'ssh root@192.168.0.119 "ansible-playbook /etc/ansible/apache-tomcat.yml --syntax-check"'
        }
      }
    stage('Ansible playbook check') {
      steps {
        sh 'ssh root@192.168.0.119 "ansible-playbook /etc/ansible/apache-tomcat.yml -C"'
        }
      }
    stage('Executing ansible playbook') {
      steps {
        sh 'ssh root@192.168.0.119 "ansible-playbook /etc/ansible/apache-tomcat.yml"'
        }
      }
    stage('Cleaning Ansible Playbook') {
      steps {
        sh 'ssh root@192.168.0.119 "rm -rf /etc/ansible/*apache-tomcat*"'
        }
      }
    }  
 }
