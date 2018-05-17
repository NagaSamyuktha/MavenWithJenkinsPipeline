pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'nohup mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                sh 'nohup mvn test'
            }
        }
    }
}
