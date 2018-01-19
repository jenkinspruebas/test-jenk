pipeline {
    agent none
    stages {
    	stage('Build') {
    		agent { label 'jenkins-demo-slave' }
    			echo 'Desde el slave'
    			echo 'Ejecuto el comando'
    			sh 'mvn --version'
    		}

    		steps { 
    			echo 'En el build'
    		}
    	}
    }