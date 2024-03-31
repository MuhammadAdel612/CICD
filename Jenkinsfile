pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build . -t muhammadadel8/nginx-alpine:latest'
            }
        }
        stage('Run') {
            steps {
                sh 'docker run -d -p 8000:80 --name web-server muhammadadel8/nginx-alpine:latest'
            }
            }
        stage('PUSH'){
            steps {
               sh 'docker login -u muhammadadel8 -p M07@mm@d!123'
                sh 'docker push muhammadadel8/nginx-alpine:latest'
        }
}
}
    }
