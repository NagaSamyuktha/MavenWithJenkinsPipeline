pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
               nohup sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
               nohup sh 'mvn test'
            }
        }
    }
}
