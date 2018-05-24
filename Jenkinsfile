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
			    emailext ( 
		       subject: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'", 
		       body: """<p>STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
			 <p>Check console output at "<a href="${env.BUILD_URL}">${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>"</p>""",
		       recipientProviders: "edara.nagasamyuktha@gmail.com,badal.singh2432@gmail.com"
		     )
		    }
	    }
    }
}
