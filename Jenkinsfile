pipeline {
    environment { 
      registry = "docker.io/muhammadadel8"
      registryCredential = 'dockerhub_id'
      }
    
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build . -t muhammadadel8/nginx-alpine:latest'
            }
        }
        stage('Run') {
            steps {
                sh 'docker run -d -p 8000:80 --name muhammadadel8/nginx-alpine:latest'
            }
            }
        stage('PUSH'){
            steps {
               script {
                docker.withRegistry( '', registryCredential ) {
                dockerImage.push()
}
        }
}
}
    }
}
