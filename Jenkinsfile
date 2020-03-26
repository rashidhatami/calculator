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
                                        sh 'mvn test'
					publishHTML (target: [
					reportDir: 'target/site/jacoco',
					reportFiles: 'index.html',
					reportName: "Html jacoco Report"
					])
                                }
            }
		stage("Code Coverage: 90%") {
				                steps {
				                        
							publishHTML (target: [
							reportDir: 'target/site/jacoco',
							reportFiles: 'index.html',
							reportName: "Html of jacoco Report"
							])
							sh 'mvn clean verify'
					
				                }
			    }
    }
}
