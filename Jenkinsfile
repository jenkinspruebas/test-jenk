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

    	stage('Probando node') {
    		node('node'){
			    stage 'input'
			    def userPasswordInput = input(
			        id: 'Password', message: 'input your password: ', ok: 'ok', parameters: [string(defaultValue: 'master', description: '.....', name: 'LIB_TEST')]
			    )
			    echo ("Password was: " + userPasswordInput)
			}
    	}
    }

    node {
		stage 'input'
		def userPasswordInput = input(
		id: 'Password', message: 'input your password: ', ok: 'ok', parameters: [string(defaultValue: 'master', description: '.....', name: 'LIB_TEST')]
		)
		echo ("Password was: " + userPasswordInput)
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