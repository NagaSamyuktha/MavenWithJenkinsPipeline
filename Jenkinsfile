pipeline {
    agent any
	environment 
	{
		def notifyStarted() {
		   // send to Slack 
		   slackSend (color: '#FFFF00', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})") 
		   // send to HipChat 
		   hipchatSend (color: 'YELLOW', notify: true, 
		       message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})" 
		     ) 

		   // send to email
		   emailext ( 
		       subject: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'", 
		       body: """<p>STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
			 <p>Check console output at "<a href="${env.BUILD_URL}">${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>"</p>""",
		       recipientProviders: "edara.nagasamyuktha@gmail.com,badal.singh2432@gmail.com"
		     )
		 }	
	}
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
