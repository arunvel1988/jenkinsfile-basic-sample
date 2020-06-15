node {
 	// Clean workspace before doing anything
    deleteDir()

    try {
        stage ('Clone') {
        	checkout scm
        }
        stage ('Build') {
        	sh "echo 'shell scripts to build project demo...'"
        }
        stage ('Tests') {
	        parallel 'static': {
	            sh "echo 'shell scripts to run static tests project demo...'"
	        },
	        'unit': {
	            sh "echo 'shell scripts to run unit tests project demo...'"
	        },
	        'integration': {
	            sh "echo 'shell scripts to run integration tests project demo...'"
	        }
        }
      	stage ('Deploy') {
            sh "echo 'shell scripts to deploy to server project demo...'"
      	}
    } catch (err) {
        currentBuild.result = 'FAILED'
        throw err
    }
	post {
		always {
		        sh "echo 'post demo'"
		}
    
	}
}




