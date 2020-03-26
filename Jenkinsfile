pipeline {
    agent any
    stages {
            
            stage("Compile") {
                                steps {
                                        sh 'mvn compile'
                                }
            }
            stage("Test") {
                                steps {
                                        sh 'mvn clean test'
					publishHTML (target: [
					reportDir: 'target/site/jacoco',
					reportFiles: 'index.html',
					reportName: "Code conerage Report"
					])
                                }
            }
		stage("Code Coverage: 90%") {
				                steps {
							sh 'mvn verify'
					
				                }
			    }
    }
}
