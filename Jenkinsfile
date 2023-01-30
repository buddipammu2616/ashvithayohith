pipeline{
    
    agent any
    environment {
        PATH = "/opt/maven3.6/bin/:$PATH"
    }
    
    stages {
        
        stage('Git Checkout'){
            
            steps{
                
                script{
                    
                    git branch: 'master', url: 'https://github.com/buddipammu2616/ashvithayohith.git'
                }
            }
        }
        stage('UNIT testing'){
            
            steps{
                
                script{
                    
                    sh 'mvn test'
                }
            }
        }
        stage('Integration testing'){
            
            steps{
                
                script{
                    
                    sh 'mvn verify -DskipUnitTests'
                }
            }
        }
        stage('build code') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('static code analysis') {
            steps {
                withSonarQubeEnv(credentialsId: 'sonar-key') {
                    sh 'mvn clean package sonar:sonar' 
                }
            
            }
            
        }
        
    }
}
