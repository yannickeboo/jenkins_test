pipeline {
    agent any 
    stages {
        stage('Checkout code') {
        steps {
           sh 'git clone https://github.com/yannickeboo/terraform_buckets.git'
        }
    }
        stage('Example Build') {
             
            steps {
                echo 'Hello, Maven'
            
            }
        }
        stage('Example Test') {
           
            steps {
                echo 'Hello, JDK'
                sh 'java -version'
            }
        }
    }
}
