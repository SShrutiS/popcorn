pipeline {
  agent any
  environment {
   DOCKER_PASSWORD = credentials('DOCKER_PASSWORD')
 }
  stages {
    stage('greeting') {
      steps {
        sh '''echo "hi world"
'''
      }
    }

    }  
    stage('build docker') {
      steps {
        sh '''docker build -t shruti17/popcorn:$BUILD_NUMBER .
'''
      }
    
    stages {
    stage('testing') {
      steps {
        sh '''docker run shruti17/popcorn:$BUILD_NUMBER rails test
'''
      }
      
    }
    stage('docker push') {
      steps {
        sh '''docker login -u shruti17 -p $DOCKER_PASSWORD
docker push shruti17/popcorn:$BUILD_NUMBER'''
      }
    }
  }
}