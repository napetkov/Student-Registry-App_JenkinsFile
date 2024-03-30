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
        stage('Deploy docker image tests') {
            steps {
            bat 'docker build -t napetkov/student_app:%BUILD_NUMBER% .'
            // bat 'docker login -u %user%--password %pass%'
            bat 'docker push napetkov/student_app:%BUILD_NUMBER%'
            bat 'docker tag napetkov/student_app:%BUILD_NUMBER% napetkov/student_app:latest'
            bat 'docker push napetkov/student_app:latest'
            }
        }
         stage('Pull and run docker container') {
            steps {
            bat 'docker pull napetkov/student_app'
            bat 'docker-compose up -d' 
            }
        }
    }
}
