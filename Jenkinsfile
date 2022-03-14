pipeline {
    agent any 
    stages {
        stage('Checkout code') {
        steps {
           sh 'git clone https://github.com/yannickeboo/terraform_buckets.git'
        }
    }
        stage('cd') {
        steps {
           sh 'cd terraform_buckets'
           sh 'terraform init'
           sh 'terraform plan > one.txt'
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
