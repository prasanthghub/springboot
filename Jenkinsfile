pipeline {
  agent any

  stages {
    stage('Checkout') {
      agent { label 'git-node' }
      steps {
        git branch: 'main', url: 'https://github.com/prasanthghub/springboot.git'
      }
    }
    stage('Build') {
      parallel {
        stage('Slave-1') {
          agent { label 'node1' }
          steps {
            sh 'mvn clean install'
          }
        }
        stage('Slave-2') {
          agent { label 'node2' }
          steps {
            sh 'mvn clean install'
          }
        }
      }
    }
  }
}
