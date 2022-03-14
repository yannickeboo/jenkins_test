pipeline {
    agent any 
    stages {
        stage('Checkout code') {
        steps {
            checkout scm
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
