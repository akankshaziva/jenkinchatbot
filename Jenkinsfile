pipeline {
	
	agent any
	
	stages {
		
		stage("build") {
		
			steps {
				git branch: 'main', url: 'https://github.com/akankshaziva/jenkinchatbot.git'
				sh 'pwd'
			 
			}
		}
		
		stage("test") {
		
			steps {
				sh ' cd /var/lib/jenkins/workspace '
			 
			}
		}
		
		stage("deploy") {
		
			steps {
				sh '''
				pip3 install httplib2
				python3 quickstart.py
				'''
			 
			}
		}
	}
}
