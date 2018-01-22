pipeline {
    agent none
    options {
    	timestamps()
    }
    stages {
    	stage('Build') {
    		agent { label 'jenkins-demo-slave' }
    			when {
    				branch 'master'
    			}
    			input {
    				message "Should we continue?"
    				ok "Yes"
    			}
    			steps {
	    			echo 'Desde el slave'

	    			script {
		    			def browsers = ['chrome', 'firefox']
	                    for (int i = 0; i < browsers.size(); ++i) {
	                    echo "Probando script, ${browsers[i]} browser"
	                }
	    		}
	   			echo 'Ejecuto el comando'
	    		echo 'En el build'
    		}
    	}
    	stage('Test') {
    		agent { label 'master' }
    		steps {
				echo 'En test'
    		}
    	}
    	stage ('a stage holding a node') {
		    steps {
		    	node ('slave'){
			        // do stuff here
			        stage 'input'
    def userPasswordInput = input(
        id: 'userPasswordInput', message: 'your password', parameters: [
            [$class: 'TextParameterDefinition', defaultValue='mb', description: 'vbn', name: 'password']
        ]
    )
    echo ("Password was: " + userPasswordInput)
		    	}
		    	echo 'Hola'
		    }
		}
    }

    post {
    	always {
    		echo 'Siempre'
    	}
    	changed {
    		echo 'En cambios'
    	}
    	failure	{
    		echo 'Si falla'
    	}
    	success {
    		echo 'Si funciona'
    	}
    	unstable {
    		echo 'Versión inestable'
    	}
    	aborted {
    		echo 'Cancelado manualmente'
    	}
    }
}