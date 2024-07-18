pipeline {
    agent any
    tools {
        nodejs 'nodeJS-byme'
    }
    stages {
        //stage('build') {
            //steps {
              //  echo 'building the application..'
                //sh 'npm install'
                //sh 'npm build'
            //}
        //}
        stage('test') {
            steps {
                script{
                    dir("app") {
                        sh "npm install"
                        sh "npm run test"
                    }
                }
            }
        }
        stage('build image') {
            steps {
                script{
                    echo 'building the docker image..'
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-repo',passwordVariable: 'PASS', usernameVariable: 'USER')]){
                        sh 'docker build -t cnwagba/jenkins-repo-dockerhub:node-1.0 .'
                        sh 'echo $PASS | docker login -u $USER --password-stdin'
                        sh 'docker push cnwagba/jenkins-repo-dockerhub:node-1.0'
                    }
                        //sh 'npm install'
                }        //sh 'npm build'
            }
        }
        stage('deploy') {
            steps {
                echo 'Hello, deploying application'
            }
        }
    }
}
