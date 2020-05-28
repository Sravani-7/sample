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
                sh 'docker images'
                sh 'docker build -t kmadhavi447/node-web-app .'
                sh 'docker images'
                
            }
        }
        stage('push docker image') {
            steps {
                withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerhubPwd')]) {
                    sh "docker login -u kmadhavi447 -p ${dockerhubPwd}"
                }
                sh 'docker tag kmadhavi447/node-web-app kmadhavi447/node-web-app'
                sh 'docker push kmadhavi447/node-web-app'
            }
        }
    }
}
