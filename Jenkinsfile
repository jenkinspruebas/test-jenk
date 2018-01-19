pipeline {
    agent none
    stages {
    	stage('Build') {
    		agent { label 'jenkins-demo-slave' }
    			when {
    				branch 'master'
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