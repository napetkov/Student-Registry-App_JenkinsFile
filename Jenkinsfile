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
        stage('NPM deploy docker image tests') {
            steps {
            docker build -t napetkov/student_app:%BUILD_NUMBER% .
            docker login -u %user%--password %pass%
            docker push napetkov/student_app:%BUILD_NUMBER%
            docker tag napetkov/student_app:%BUILD_NUMBER% napetkov/student_app:latest
            docker push napetkov/student_app:latest
            }
        }
    }
}
