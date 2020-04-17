pipeline {
	agent {
		docker {
			image 'node:6-alpine'
		}
	}
	environment {
		CI = 'true'
	}
	stages {
		stage('Build') {
			steps {
				sh 'npm install'
			}
		}
		stage('Deliver') {
			steps {
				input message: 'Pret a delivrer l application ?'
			}
		}
		stage('Ansible installation'){
			steps {
				script {
					sh 'apk add ansible'
				}
				script {
					sh 'apk add python3'
				}
			}
		}
		stage('Ansible init') {
			steps {
				script {
					sh 'ansible --version'
				}
			}
		}
		stage(' Ansible - test') {
			steps {
				dir('dev/ansible'){
					sh 'ansible all -m ping'
				}
			}
		}
	}
}
