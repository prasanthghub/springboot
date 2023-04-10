pipeline {
  agent none
  
  stages {
    stage('Build on Slave-1') {
      agent {
        label 'node1'
      }
      steps {
        sh 'git clone https://github.com/prasanthghub/springboot.git'
        sh 'cd springboot && ./build.sh'
      }
    }
    stage('Build on Slave-2') {
      agent {
        label 'node2'
      }
      steps {
        sh 'git clone https://github.com/prasanthghub/springboot.git'
        sh 'cd springboot && ./build.sh'
      }
    }
  }
}
