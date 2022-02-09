def notifyBuild(String buildStatus = 'Started'){
	buildStatus =  buildStatus ?: 'Successful'
		emailext to:  "${env:EMAIL_RECIPIENTS}",
		mimeType: 'text/html',
		subject: "Build ${BUILD_NUMBER}  " + buildStatus + " (${currentBuild.fullDisplayName})",
		body: "<!DOCTYPE html><html><head> <style>table, th, td{border: 2px solid black;border-collapse: collapse;}th, td{padding: 15px;}.tableLableLeft{font-family: Calibri;font-size: 18px;font-weight: bold;}.tableLableRight{font-family: Calibri; font-size: 18px;}</style> </head> <body> <p class='tableLableLeft'>" + "Build ${BUILD_NUMBER} - " + buildStatus + " (${currentBuild.fullDisplayName})" + "</p><table style='width:100%'> <tr> <td class='tableLableLeft'>Build Number</td><td class='tableLableRight'>${BUILD_NUMBER}</td></tr><tr> <td class='tableLableLeft'>Build Log</td><td class='tableLableRight'>${BUILD_URL}console</td></tr><tr> <td class='tableLableLeft'>Changes</td><td class='tableLableRight'>" + getChangeString() + "</td></tr></table> </body></html>",
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
		}
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
}
			

