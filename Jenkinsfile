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
		    			/*def browsers = ['chrome', 'firefox']
	                    for (int i = 0; i < browsers.size(); ++i) {
	                    echo "Probando script, ${browsers[i]} browser"
	                	}*/

	                	def userInput = input(
	                    	id : 'userInput', 
	                    	message: 'Input something', 
	                    	parameters: [
	                    		[$class: 'TextParameterDefinition', defaultVaue: '', description: 'Input text', name: 'inputText']
	                    	]
	                    )
	                    echo ("Text: " + userInput)
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