pipeline {
    agent any
    stages {
        stage('compile') {
	   steps {
                echo 'compiling..'
		git url: 'https://github.com/tejaswini39/samplejavaapp.git'
		sh script: '/opt/maven/bin/mvn compile'
           }
        }
        
        stage('unit-test') {
	   steps {
                echo 'unittest..'
	        sh script: '/opt/maven/bin/mvn test'
                 }
	   post {
               success {
                   junit 'target/surefire-reports/*.xml'
               }
           }			
        }
       
        stage('package') {
	   steps {
                echo 'package..'
		sh script: '/opt/maven/bin/mvn package'	
           }		
        }
    }
}
