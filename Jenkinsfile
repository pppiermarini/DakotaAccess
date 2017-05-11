pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/pppiermarini/DakotaAccess.git', branch: 'master', poll: true)
      }
    }
    stage('Build') {
      steps {
        git(url: 'https://github.com/pppiermarini/DakotaAccess.git', branch: 'master')
        sh '''echo add maven build
pwd
ls'''
        dir(path: 'desktop-console-java-master') {
          sh 'mvn clean package'
        }
        
      }
    }
    stage('Test') {
      steps {
        sleep 5
      }
    }
  }
}