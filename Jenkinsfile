pipeline {
    agent any 
        options {
            buildDiscarder(logRotator(numToKeepStr: '5'))
        }
        environment {
            DOCKERHUB_CREDENTIALS = credentials('lakshmi039-dockerhub')
        }
        stages {
            stage('build'){
                steps {
                    sh 'docker build -t lakshmi039/kaniyam:latest .'
                }
            }
            stage('login') {
                steps {
                    sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                }
            }
            stage('push') {
                steps {
                    sh 'docker push lakshmi039/kaniyam:latest'  
                }
            }
        }
        post {
            always {
                sh 'docker logout'
            }
        }
}

