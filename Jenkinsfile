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
	    			echo 'Ejecuto el comando'
	    			echo 'En el build'
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