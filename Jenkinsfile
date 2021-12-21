pipeline {
    agent any
    stages {
        stage('compile') {
	   steps {
                echo 'compiling..'
		git url: 'https://github.com/lerndevops/DevOpsClassCodes'
		sh script: '/opt/apache-maven-3.6.3/bin/mvn compile'
           }
        }
        
        stage('unit-test') {
	   steps {
                echo 'unittest..'
	        sh script: '/opt/apache-maven-3.6.3/bin/mvn test'
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
		sh script: '/opt/apache-maven-3.6.3/bin/mvn package'	
           }		
        }
    }
}
