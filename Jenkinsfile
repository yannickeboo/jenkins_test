pipeline {
  agent any
  tools {
        terraform 'terraform'
    } 
  environment {
        def BUILDVERSION = sh(returnStdout: true, script: 'date +%Y-%m-%d').trim()
    }
  stages{
    stage('clean workspace') {
      steps {
        cleanWs()
      }
    }
    stage('checkout') {
      steps {
        sh 'git clone https://github.com/yannickeboo/terraform_buckets.git'
      }
    }
    stage('terraform') {
      steps {
        sh './terraformw apply -auto-approve -no-color'
      }
    }
  }
  post {
    always {
      cleanWs()
      sh 'rm -fr terraform_buckets'


    }
  }
}