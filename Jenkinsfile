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
    }
}
