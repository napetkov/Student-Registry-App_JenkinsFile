pipeline {
    agent any
    stages {
        stage('NPM Install') {
            steps {
                bat 'npm install'
            }
        }
        stage('NPM Audit') {
            steps {
                bat 'npm audit'
            }
        }
        stage('NPM Integation tests') {
            steps {
            bat 'npm run test'
            }
        }
    }
}
