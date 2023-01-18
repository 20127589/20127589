pipeline {
    agent {
        label 'docker'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Docker Build') {
            steps {
                sh "docker build -t myimage:$BUILD_NUMBER ."
            }
        }
        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh "docker login -u $USERNAME -p $PASSWORD"
                    sh "docker push myimage:$BUILD_NUMBER"
                }
            }
        }
    }
}
