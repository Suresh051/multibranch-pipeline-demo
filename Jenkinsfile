pipeline {

    agent any

    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '16', 
                    numToKeepStr: '10'
            )
    }

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()           
                echo "Cleaned Up Workspace For Project"
            
            }
        }

        stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/spring-projects/spring-petclinic.git']]
                ])
            }
        }

        stage(' Unit Testing') {
            steps {        
                echo "Running Unit Tests"
            
            }
        }

        stage('Code Analysis') {
            steps {   
                echo "Running Code Analysis"
            }
        }

        stage('Build Deploy Code To Dev') {
            when {
                branch 'develop'
            }
            steps {           
                echo "Building Artifact"          
                echo "Deploying Code on Dev"
             
            }
        }
		stage('Build Deploy Code to QA ') {
            when {
                branch 'qa'
            }
            steps {           
                echo "Building Artifact"          
                echo "Deploying Code on qa"
             
            }
        }

    }   
}
