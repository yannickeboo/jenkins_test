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
               sh label: '',script: 'terraform init'
               }
        }
    }
        stage('cd ..') {
        steps {
           sh 'cd ..'
           sh 'rm -rf terraform_buckets'
    
        }
    }   
        
    }
}
