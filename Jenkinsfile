pipeline {
    agent {
        docker { image 'node:17' }
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '5', daysToKeepStr: '1'))
        disableConcurrentBuilds()
    }
    stages {
        stage('Install') {
            steps {
              sh "npm install"
            }
        }
        // stage('Build') {
        //     steps {
        //       sh "npm run build"
        //     }
        // }
        stage('Chromatic Check') {
            environment {
              CHROMATIC_PROJECT_TOKEN = 'd98261d7de72'
            }
            steps {
              sh "npm run chromatic --project-token=${CHROMATIC_PROJECT_TOKEN}"
            }
        }
    }
}