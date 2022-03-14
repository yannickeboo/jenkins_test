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
           sh 'mkdir -p creds'
           sh 'echo $SVC_ACCOUNT_KEY | base64 -d > ./creds/serviceaccount.json'
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
