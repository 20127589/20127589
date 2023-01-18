pipeline {
    agent none
    stages {
        stage('Build') {
            steps {
                node {
                    label 'docker'
                    sh 'mvn clean install'
                }
            }
        }
        stage('Docker Build') {
            steps {
                node {
                    label 'docker'
                    sh "docker build -t myimage:$BUILD_NUMBER ."
                }
            }
        }
        stage('Docker Push') {
            steps {
                node {
                    label 'docker'
                    withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                        sh "docker login -u $USERNAME -p $PASSWORD"
                        sh "docker push myimage:$BUILD_NUMBER"
                    }
                }
            }
        }
    }
}
