pipeline {
  environment {
    registry = "muhammadadel8/newnginx"
    registryCredential = 'dockerhub_id'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git([url: 'https://github.com/MuhammadAdel612/CICD.git', branch: 'main'])
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Deploy to K8s') {
      steps{
        script {
          sh "sed -i -e 's/29/$BUILD_NUMBER/'
          sh "cat deployment.yml"
          sh "kubectl --kubeconfig=/kubeconfig get pods"
          sh "kubectl --kubeconfig=/kubeconfig apply -f deployment.yml"
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}
