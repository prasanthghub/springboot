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
    stage('Build') {
      parallel {
        stage('Slave-1') {
          agent { label 'node1' }
          steps {
            sh 'mvn compile'
          }
        }
        stage('Slave-2') {
          agent { label 'node2' }
          steps {
            sh 'mvn compile'
          }
        }
      }
    }
  }
}
