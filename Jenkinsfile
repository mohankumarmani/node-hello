//Jenkins file for eci-adapter-yardcrane micro service

pipeline {
    agent {
        label 'chn-linux' 
    }
    stages {
        stage('Clean') {
            steps {
                sh "hostname"
                
            }
        }
        stage('Test npm') {
            steps {
                sh "node --version"
			    }
        }

        stage('Test Docker') {
            steps {
                echo 'docker test'
                sh "docker ps"
            }
        }

        stage('Nexus Upload') {
            steps {
                echo "Publishing Branch" 
                sh "docker build -t test1 ."
            }
        }

    }

}