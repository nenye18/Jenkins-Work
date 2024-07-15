pipeline {
    agent any
    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 1, unit: 'SECONDS')
    }
    stages {
        stage('build') {
            steps {
                echo 'building the application..'
                //sh 'npm install'
                //sh 'npm build'
            }
        }
        stage('test') {
            steps {
                echo 'Hello, testing application'
            }
        }
        stage('deploy') {
            steps {
                echo 'Hello, deploying application'
            }
        }
    }
}
