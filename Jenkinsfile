pipeline {
    agent none
    stages {
    	stage('Build') {
    		agent { label 'jenkins-demo-slave' }
    			steps {
	    			echo 'Desde el slave'
	    			echo 'Ejecuto el comando'
	    			echo 'En el build'
    			}
    		}
    	}
    }