pipeline {
    agent {
        docker {
            image 'maven:3.8.7-eclipse-temurin-11'
            args '-v $HOME/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B'
            }
        }
    }
}
