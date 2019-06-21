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

        stage('Docker build') {
            steps {
                echo "Docker build" 
				sh "$(aws ecr get-login --no-include-email --region ap-south-1)"
                sh "docker build -t test1 ."
				sh "docker tag devopstest:latest 128144341703.dkr.ecr.ap-south-1.amazonaws.com/devopstest:latest"
            }
        }
		
		stage('Docker push') {
            steps {
                echo "Docker push" 
                sh "docker push 128144341703.dkr.ecr.ap-south-1.amazonaws.com/devopstest:latest"
            }
        }

    }

}