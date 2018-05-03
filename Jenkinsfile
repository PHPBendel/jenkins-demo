pipeline {
    agent any
    stages {
        stage('No-op') {
            steps {
                sh 'ls'
            }
        }
    }
    post {
            always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
	mail to: 'pedro.bendel@gmail.com',
        subject: "Success Pipeline: ${currentBuild.fullDisplayName}",
        body: "Something is right with ${env.BUILD_URL}"
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