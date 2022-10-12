pipeline {
    agent any
    environment {
    DOCKERHUB_CREDENTIALS = credentials('aksh-dockerhub')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/wagh96/first-repo.git'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t aksh31/akshrepo:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'docker login -u aksh31 -p dckr_pat_P2723qZ-cAw2lMgVwLJdvu-Yh5k'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push aksh31/akshrepo:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
