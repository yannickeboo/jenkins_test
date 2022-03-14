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
           sh 'cp /var/jenkins_home/main-aspect-341416-dff3a9baea19.json /var/jenkins_home/workspace/test38/terraform_buckets/'
           sh 'cd terraform_buckets'
           sh 'pwd'
           dir("${env.WORKSPACE}/terraform_buckets"){
               sh 'pwd'
               
               sh label: '',script: 'terraform init'
               }
        }
    } 
    }  
        
}
