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
				sh "yum install nodejs"
			    sh "yum install npm"
            }
        }

        stage('Jar') {
            steps {
                echo 'Building javadoc jar'
                sh "docker ps"
            }
        }

        stage('Nexus Upload') {
            environment {
                // JENKINS_USER_CREDS = credentials('8984949d-8408-4137-a5ba-e8655d9beeba')
                // New identical credentials to above with "readable" id
                JENKINS_USER_CREDS = credentials('jenkins-ldap-user-password')
                //echo "username: ${JENKINS_USER_CREDS_USR}"
                ENV_NAME = "${env.BRANCH_NAME}"
            }
            when {
                branch 'develop'
           }
            steps {
                echo 'Publishing Branch: ' + ENV_NAME
                sh "./gradlew publish -PuploadRepoUsername=$JENKINS_USER_CREDS_USR -PuploadRepoPassword=$JENKINS_USER_CREDS_PSW"
            }
        }

    }

}