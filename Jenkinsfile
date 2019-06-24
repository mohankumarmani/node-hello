//Jenkins file for eci-adapter-yardcrane micro service

pipeline {
    agent {
        label 'chn-linux' 
    }
    stages {
        stage('Clean') {
            steps {
                sh "docker system prune -a"
                
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
                sh "docker version"
            }
        }

        stage('Docker build') {
            steps {
                echo "Docker build" 
				sh "$(aws ecr get-login --no-include-email --region us-east-1)"
                sh "docker build -t devopstest ."
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