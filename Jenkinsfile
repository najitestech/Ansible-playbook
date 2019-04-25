pipeline {
  environment {
        ansible = "192.168.0.119"
    }
  agent any
  
  stages {
    stage('Copying playbook for tomcat') {
      steps {
        echo 'host: ${host}'
        sh 'scp ./apache-tomcat.yml root@$ansible:/etc/ansible'
        }
      }
    stage('Ansible syntax check') {
      steps {
        sh 'ssh root@$ansible "ansible-playbook /etc/ansible/apache-tomcat.yml --syntax-check"'
        }
      }
    stage('Ansible playbook check') {
      steps {
        sh 'ssh root@$ansible "ansible-playbook /etc/ansible/apache-tomcat.yml -C"'
        }
      }
    stage('Executing ansible playbookfor for tomcat') {
      steps {
        sh 'ssh root@$ansible "ansible-playbook /etc/ansible/apache-tomcat.yml"'
        }
      }
    stage('Cleaning Ansible Playbook') {
      steps {
        sh 'ssh root@$ansible "rm -rf /etc/ansible/*apache-tomcat*"'
        }
      }
    stage('SUCCESS!!!') {
      steps {
        sh 'echo pipeline completed seccesfuly'
        }
      }
    }  
 }
