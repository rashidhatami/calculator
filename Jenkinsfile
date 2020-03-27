pipeline {
    agent any
		triggers {
		pollSCM('* * * * *')
		}
    stages {
            
            stage("Compile") {
                                steps {
                                        sh 'mvn compile'
                                }
            }
            stage("Test") {
                                steps {
                                        sh 'mvn test'
					publishHTML (target: [
					reportDir: 'target/site/jacoco',
					reportFiles: 'index.html',
					reportName: "Code coverage Report"
					])
                                }
            }
		stage("Code Coverage: 90%") {
				                steps {
							sh 'mvn verify'
					
				                }
			    }
    }
	post {
	always {
		mail to: 'rashid.khatami@gmail.com',
		subject: "Completed Pipeline: ${currentBuild.fullDisplayName}",
		body: "Your build completed, please check: ${env.BUILD_URL}"
	}
}
}
