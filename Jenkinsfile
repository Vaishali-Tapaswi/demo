
pipeline {
    agent any
    tools { 
        maven 'maven3.8' 
	jdk "jdk11"
    }

    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '15', 
                    numToKeepStr: '10'
            )
    }

    environment {
        APP_NAME = "DEMO"
        APP_ENV  = "DEV"
    }

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                echo "Cleaned Up Workspace for ${APP_NAME}"
                
            }
        }

        stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/Vaishali-Tapaswi/javademo']]
                ])
            }
        }

        stage('Code Build') {
            steps {
                 bat 'mvn install package'
            }
        }
		}   
}
