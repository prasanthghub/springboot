pipeline {
	agent any
	tools {
    	maven 'my_mvn'
	}
	stages {
    	stage("Checkout") {   
        	steps {               	 
            	git branch: 'main', url: 'https://github.com/prasanthghub/springboot.git'
            }
        }
        
         stage('Compile and Test (Node 1)') {
            agent {
                node {
                    label 'node1'
                }
            }
            steps {
                sh 'mvn clean compile test'
            }
        }
        
        stage('Compile and Test (Node 2)') {
            agent {
                node {
                    label 'node2'
                }
            }
            steps {
                sh 'mvn clean compile integration-test'
            }
        }
        
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts 'target/*.jar'
            }
        }
        
        stage('Publish Test Reports') {
            steps {
                junit 'target/surefire-reports/*.xml'
                junit 'target/failsafe-reports/*.xml'
            }
        }
        
        stage('Notify') {
            steps {
                // send email, post to Slack, etc.
            }
        }
    }
}
