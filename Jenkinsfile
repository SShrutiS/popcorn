pipeline {
  agent any
  
  environment {
    Docker_password = credentials('Docker_password')
  }
  
  stages {
    stage('greeting') {
      steps {
        sh 'echo "hello world"'
      }
    }
    
    
    stage('build docker/add container') {
      steps {
        sh 'docker build -t shruti17/popcorn:$BUILD_NUMBER .'
      }
    }
    
    stage('testing') {
      steps {
        sh '''docker run shruti17/popcorn:$BUILD_NUMBER rails test'''
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