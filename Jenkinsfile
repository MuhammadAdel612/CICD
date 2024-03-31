pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker rmi nginx-alpine:latest'
                sh 'docker build . -t nginx-alpine'
            }
        }
        stage('Run') {
            steps {
                sh 'docker run -d -p 8000:80 --name web-server nginx-alpine'
            }
        stage('PUSH'){
                sh 'docker tag nginx-alpine:latest muhammadadel8/nginx-alpine:latest'
                sh 'docker push muhammadadel8/nginx-alpine:latest'
        }
    }
}
}
