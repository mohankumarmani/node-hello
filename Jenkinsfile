//Jenkins file for eci-adapter-yardcrane micro service

pipeline {
    agent {
        label 'linux' 
    }
    stages {
        stage('Clean') {
            steps {
                sh "hostname"
                
            }
        }
        stage('Compile') {
            steps {
                sh "curl -sL https://rpm.nodesource.com/setup_10.x | sudo bash -"
				sh "yum install nodejs -y"
			    }
        }

        stage('Jar') {
            steps {
                echo 'Building javadoc jar'
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