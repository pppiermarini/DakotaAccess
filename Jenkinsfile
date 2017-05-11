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
      }
    }
    stage('Test') {
      steps {
        sleep 5
      }
    }
  }
}