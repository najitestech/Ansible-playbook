pipeline {
  agent any
  
  stages {
    stage('Copying playbook') {
      steps {
        sh ' scp ./apache-tomcat.yml root@192.168.0.119:/etc/ansible'
        }
      }
    }  
 }
