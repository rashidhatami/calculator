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
                                }
            }
		stage("Code Coverage: 90%") {
				                steps {
				                        sh 'mvn clean verify'
				                }
			    }
    }
}
