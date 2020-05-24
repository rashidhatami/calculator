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
		stage("Code Coverage: 50%") {
				                steps {
							sh 'mvn verify'
					
				                }
			    }
		stage("Package") {
			steps {
				sh "mvn package"
			}
		}
		stage("Docker build") {
			steps {
				sh "docker build -t localhost:5000/calculator ."
			}
		}
    
		stage("Credential Registry") {
			steps {
				sh "docker login localhost:5000 --username niki --password hatami"
			}
		}

		stage("Docker push") {
			steps {
				sh "docker push localhost:5000/calculator"
			}
		}
		stage("Deploy to staging") {
			steps {
				sh "docker run -d --rm -p 8765:8080 --name calculator localhost:5000/calculator"
			}
		}
		stage("Acceptance test") {
			steps {
				sleep 60
				sh "chmod +x acceptance_test.sh && ./acceptance_test.sh"
				}
		}
}
		post {
			always {
				sh "docker stop calculator"
				}
		}	
}
