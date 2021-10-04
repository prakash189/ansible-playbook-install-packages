#!groovy
pipeline {
  agent any
  environment {
    AWS_ACCESS_KEY_ID = credentials('AWS_ACCESS_KEY_ID')
    AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_KEY')

  }
  stages {
    stage('checkout') {
     steps {

       git branch: 'main', url: 'https://github.com/prakash189/ansible-playbook-install-packages'

         }

        stage('run ansible playbook') {

            steps {
                
                sh "ansible-playbook main.yml -i hosts --user ubuntu "
        
            
            }
        }

       }
            stage('start the sonar quebe server') {
              steps {
                  sh 'mv sonarqube-* sonarqube'
                  sh 'cd sonarqube/bin/linux-x86-64/'
                  sh 'sonar.sh console &'
                }
            }

    }
}