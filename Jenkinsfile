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
    				message ""
    				id ""
    				ok ""
    				//submitter ""
    				//submitterParameter ""
    				parameters {
    					booleanParam(name: 'DEBUG_BUILD', defaultValue: true, description: 'Cosa numero 1')
    				}

    			}
    			/*input {
    				message "Should we continue?"
    				ok "Yes"
    				id "userInput1"
    				message "Input something 1"
    				ok "ok"
    				parameters {
    					string(name: 'Prueba', defaultValue: 'staging', description: '')
    				}
    			}*/
    			steps {
	    			echo 'Desde el slave'
	    			echo "params.${DEBUG_BUILD}"
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

    node {
    	    echo 'artifacts'
    		archiveArtifacts artifacts: 'output/*.txt', allowEmptyArchive: true
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