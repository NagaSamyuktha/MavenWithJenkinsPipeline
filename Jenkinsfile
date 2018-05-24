pipeline {
    agent any
    stages {
        stage('Compile') {
            steps {
                bat "mvn clean compile"
            }
        }
        stage('Test') {
            steps {
                bat "mvn test"
            }
        }
        stage('mavenBuild')
	{
		steps
		{
			bat ' mvn package'
		}
	}
	    stage('emailNotification'){
		    steps{
			    bat "mail bcc: '', body: 'testing...', cc: '', from: 'edara.nagasamyuktha@gmail.com', replyTo: 'edara.nagasamyuktha@gmail.com', subject: 'Test Email Notification From Jenkins File', to: 'edara.nagasamyuktha@gmail.com,badal.singh2432@gmail.com'"

		    }
	    }
    }
}
