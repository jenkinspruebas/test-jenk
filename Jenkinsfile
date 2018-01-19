pipeline {
    agent none
    stages {
    	stage('Build') {
    		agent { label 'jenkins-demo-slave' }
    			steps {
	    			echo 'Desde el slave'
	    			echo 'Ejecuto el comando'
	    			sh 'mvn --version'
	    			echo 'En el build'
    			}
    		}
    	}
    }