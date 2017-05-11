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
        parallel(
          "Test": {
            sleep 5
            
          },
          "Chrome": {
            sleep 10
            
          },
          "Safari": {
            sleep 12
            
          }
        )
      }
    }
    stage('Stage') {
      steps {
        sh 'echo Deploy to staging'
      }
    }
    stage('Deploy') {
      steps {
        parallel(
          "UAT": {
            input 'Proceed?'
            sh 'echo Deploy to UAT'
            
          },
          "QA": {
		    input 'Proceed?'
            sh 'echo some code here'
            
          }
        )
      }
    }
	stage('Production') {
      steps {
	  input 'Proceed?'
        sh 'echo Deploy to staging'
      }
    }
  }
}