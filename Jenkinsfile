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
	     mail to: 'pedro.bendel@gmail.com',
             subject: "Success Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is right with ${env.BUILD_URL}"
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
          echo "I succeeeded!
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