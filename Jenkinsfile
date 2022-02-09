 def notifyBuild(String buildStatus = 'Started'){
	buildStatus =  buildStatus ?: 'Successful'
		emailext to:  "${env:EMAIL_RECIPIENTS}",
		mimeType: 'text/html',
		subject: "Build ${BUILD_NUMBER}  " + buildStatus + " (${currentBuild.fullDisplayName})",
		body: "<!DOCTYPE html><html><head> Build Details</head><body><p> Build ${BUILD_NUMBER} - " + buildStatus + " (${currentBuild.fullDisplayName})"</p></body></html>		
		attachLog: true
}

pipeline {
    agent any
    stages {
		stage('GIT CHECKOUT'){
			steps{
			git branch: 'main', url: 'https://github.com/akankshaziva/jenkinchatbot.git'
			}
		}
		stage('Test '){
			steps{
				sh ' cd /var/lib/jenkins/workspace'
            
		    }
		}
		stage('Execute') {
			steps{
				sh 'pip3 install httplib2'
				sh 'python3 pythoncode.py'
	}


post { 
		success {
            notifyBuild("Successful");
				}
        unstable {
            notifyBuild("Unstable");
				}
        failure {
            notifyBuild("Failed");
				}
    }
