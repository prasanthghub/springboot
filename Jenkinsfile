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
        
        stages {
    stage('Build on Slave-1') {
      agent {
        label 'node1'
                }
            }
            steps {
                sh 'mvn clean compile '
            }
        }
        
        stage('Build on Slave-2') {
      agent {
        label 'node2'
                }
            }
            steps {
                sh 'mvn clean compile '
            }
        } 
    }
}
