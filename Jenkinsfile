pipeline {
    agent any
    tools {
        terraform 'terraform'
    } 
    stages {
        stage('Checkout code') {
        steps {
           sh 'git clone https://github.com/yannickeboo/terraform_buckets.git'
        }
    }
        stage('cd') {
        steps {
           sh 'cd terraform_buckets'
           sh 'pwd'
           dir("${env.WORKSPACE}/terraform_buckets"){
               sh 'pwd'
               sh 'mv /var/jenkins_home/main-aspect-341416-dff3a9baea19.json ${env.WORKSPACE}/terraform_buckets'
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
