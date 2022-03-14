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
           sh 'cp /var/jenkins_home/main-aspect-341416-dff3a9baea19.json /var/jenkins_home/workspace/test39/terraform_buckets/'
           sh 'cd terraform_buckets'
           sh 'pwd'
           dir("${env.WORKSPACE}/terraform_buckets"){
               sh 'pwd'
               
               sh label: '',script: 'terraform init'
               sh label: '',script: 'terraform plan -out=test1'
               sh 'cat test1'
               }
        }
    } 
        stage('remove') {
        steps {
           
           sh 'rm -fr terraform_buckets'
          
        }
    }

    }  
        
}
