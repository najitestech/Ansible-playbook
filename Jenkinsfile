pipeline {
  agent any
  environment {
        ansible = "192.168.0.119"
        tomcat = "192.168.0.21"
    }  
  stages {
    stage('Copying playbook for tomcat') {
      steps {
      //  withMaven(maven : 'maven-3.6.1') {
       //         sh 'mvn clean compile'
        sh 'echo $host'
        sh 'scp ./apache-tomcat.yml root@$ansible:/etc/ansible'
        }
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
        sh 'ssh root@$tomcat "cd /opt/tomcat/tomcat9 && ./bin/startup.sh"'
        sh 'echo pipeline completed seccesfuly'
        }
      }
    }  
 }
