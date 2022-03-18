# jenkins_test
rm -rf terraform_buckets
sh label: '',script: 'terraform plan -out=/var/jenkins_home/workspace/test41/test1'
sh label: '',script: 'terraform apply --auto-approve'
  sh 'rm -rf /var/jenkins_home/workspace/test42/terraform-refresh-$BUILDVERSION'
  ll

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
           sh 'cp /var/jenkins_home/main-aspect-341416-dff3a9baea19.json /var/jenkins_home/workspace/test47/terraform_buckets/'
           sh 'cd terraform_buckets'
           sh 'pwd'
           dir("${env.WORKSPACE}/terraform_buckets"){
               sh 'pwd'
               sh 'mkdir -p /var/jenkins_home/workspaceterra'
               sh label: '',script: 'terraform init'
               sh label: '',script: 'terraform plan -refresh-only > /var/jenkins_home/workspace/test47/terraform-refresh-$BUILDVERSION'
               
               }
        }
    } 
        stage('remove') {
        steps {
           emailext attachLog: true, body: 'email', subject: 'test2', to: 'yannickparker84@gmail.com'
           sh 'rm -fr terraform_buckets'
           sh 'cat /var/jenkins_home/workspace/test47/terraform-refresh-$BUILDVERSION'
        }
    }
        stage('slack upload file') {
        steps {
          
            slackUploadFile filePath: '/var/jenkins_home/workspace/test47/terraform-refresh-*', initialComment:  'HEY HEY'  
          
        }       
    }
        stage('delete text') {
        steps {
           sh 'cat /var/jenkins_home/workspace/test47/terraform-refresh-$BUILDVERSION'
            
        }
    }

    }  
        
}
