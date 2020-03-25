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
							publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'target/site/jacoco', reportFiles: 'index.html', reportName: 'Code Coverage Report', reportTitles: ''])
                                }
            }
		stage("Code Coverage: 90%") {
				                steps {
				                        

							sh 'mvn clean verify'
				                }
			    }
    }
}
