pipeline {
    agent any
    tools {
        terraform 'terraform'
    } 
    environment {
        def BUILDVERSION = sh(returnStdout: true, script: 'date +%Y-%m-%d').trim()
    }

    stages {
        stage('Checkout code') {
        steps {
           sh 'git clone https://github.com/yannickeboo/terraform_buckets.git'
    
           
        }
    }
        stage('cd') {
        steps {
           sh 'cp /var/jenkins_home/main-aspect-341416-dff3a9baea19.json /var/jenkins_home/workspace/test42/terraform_buckets/'
           sh 'cd terraform_buckets'
           sh 'pwd'
           dir("${env.WORKSPACE}/terraform_buckets"){
               sh 'pwd'
               sh 'mkdir -p /var/jenkins_home/workspace/test42/terra'
               sh label: '',script: 'terraform init'
               sh label: '',script: 'terraform plan -refresh-only > /var/jenkins_home/workspace/test42/terraform-refresh-$BUILDVERSION'
               
               }
        }
    } 
        stage('remove') {
        steps {
           
           sh 'rm -fr terraform_buckets'
           sh 'cat /var/jenkins_home/workspace/test42/terraform-refresh-$BUILDVERSION'
        }
    }
        stage('slack upload file') {
        steps {
          
            emailext body: '''dvnafkl 
bn\'
 NE
M''', subject: 'test', to: 'sys-eng@verve.com' 
          
        }       
    }
        stage('delete text') {
        steps {
           sh 'rm -rf /var/jenkins_home/workspace/test42/terraform-refresh-$BUILDVERSION'
            
        }
    }

    }  
        
}
