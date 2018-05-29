pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
		withCredentials([sshUserPrivateKey(credentialsId: '7144f627-4881-4b8b-b28f-12549469f5c2',\
						   keyFileVariable: 'SSH_KEY',\
						   passphraseVariable: 'SSH_PASS',\
						   usernameVariable: 'SSH_USERNAME')]) {
		    sh run-environment.sh
		    sh echo 'Hello'
		}
            }
        }
	stage('Test'){
	    
	}
	stage ('Deploy'){
	    
	}
    }
    post {
        always {
	    echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
	    echo 'I succeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
}
