pipeline {
    agent any
    stages {
        stage('verify branch') {
            steps {
                echo "$GIT_BRANCH"
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker images ls'
                sh 'docker build -t madhavi/node-web-app .'
                sh 'docker images ls'
            }
        }
        stage('push docker image') {
            steps {
                withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerhubPwd')]) {
                    sh "docker login -u kmadhavi447 -p ${dockerhubPwd}"
                }
                sh 'docker push kmadhavi447/node-web-app:1'
            }
        }
    }
}
