pipeline {
    agent { label 'linux_node'}
    // agent {
    //     docker {
    //         image 'node:lts-buster-slim'
    //         args '-p 3000:3000'
    //     }
    // }
    // environment {
    //     CI = 'true'
    // }
  tools {
    nodejs 'nodejs-16.20.2'
  }
    stages {
        stage('Clone repo'){
            steps {
                git 'https://github.com/gurleravindar/simple-node-js-react-npm-app.git'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
