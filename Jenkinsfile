pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build . -t nginx-alpine'
            }
        }
        stage('Run') {
            steps {
                sh 'docker run -d -p 8000:80 --name web-server nginx-alpine'
            }
        }
    }
}
