pipeline {
    // master executor should be set to 0
    agent any
    stages {
        stage('Build Jar') {
            steps {
                //bat - for windows
                sh "mvn clean package -DskipTests"
            }
        }
        stage('Build Image') {
            steps {
                //bat - for windows
                sh "docker build -t='newyon2014/selenium-docker' ."
            }
        }
        stage('Push Image') {
            steps {
			    withCredentials([usernamePassword(credentialsId: 'DOCKER_HUB_CRED', passwordVariable: 'pass', usernameVariable: 'user')]) {
                    //bat - for windows
			        sh  "docker login --username=${user} --password=${pass}"
			        sh  "docker push newyon2014/selenium-docker"
			    }                           
            }
        }
    }
}
