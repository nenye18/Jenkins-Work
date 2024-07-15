pipeline {
    agent any
    environment {
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('server-credentials')
    }
    //tools {
      //  FIND OUT HOW TO ADD NPM 
    //}
    stages {
        stage("build npm") {
            steps {
                script{
                    sh "npm build"
                }

            }
        stage('build image') {
            steps {
                script{
                    echo "building docker image"
                    withCredentials([usernamePassword(credentialsId: 'docker hub repository',passwordVariable: 'PASS',usernameVariable: 'USER')]){
                        sh 'docker build -t cnwagba/jenkins-repo-dockerhub:npm-3.0 .'
                        sh 'echo $PASS | docker login -u $USER --password-stdin'
                        sh 'docker push cnwagba/jenkins-repo-dockerhub:npm-3.0'
                    }
                }
            }
        }
        stage('test') {
            steps {
                echo 'Hello, testing application'
            }
        }
        stage('deploy') {
            steps {
                script {
                    echo "deploying application"
                    
                }
                
            }
        }
    
}
