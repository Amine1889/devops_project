pipeline {
    agent any

    tools {
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }

    stages {

        stage('GIT') {
            steps {
                git branch: 'main',
                url: 'https://github.com/BoRedo-64/devops.git'
            }
        }

        stage('Compile Stage') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t yahyabichiou/devops-app:1.0 .'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker login -u yahyabichiou -p Bichiou2003'
                sh 'docker push yahyabichiou/devops-app:1.0'
            }        
        }

    }
}
