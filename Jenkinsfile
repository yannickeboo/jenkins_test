pipeline {
    agent any
    tools {
        terraform 'terraform'
    } 
    environment {
    SVC_ACCOUNT_KEY = credentials('sa-key')
  }

    stages {
        stage('Checkout code') {
        steps {
           sh 'git clone https://github.com/yannickeboo/terraform_buckets.git'
    
           sh 'cp ~/var/jenkins_home/main-aspect-341416-dff3a9baea19.json /var/jenkins_home/workspace/test32/terraform_buckets'
        }
    }
        stage('cd') {
        steps {
           sh 'cd terraform_buckets'
           sh 'pwd'
           dir("${env.WORKSPACE}/terraform_buckets"){
               sh 'pwd'
               
               sh label: '',script: 'terraform init'
               }
        }
    }
        stage('m') {
        steps {
           sh 'cd ..'
           sh 'cd ..'
    
        }
    }   
        
    }
}
