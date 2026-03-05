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
                url: 'https://github.com/Amine1889/devops_project.git'
            }
        }

        stage('Compile Stage') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t amine311002/devops-app:1.0 .'
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker login -u amine311002 -p Amine1234'
                sh 'docker push amine311002/devops-app:1.0'
            }      
         stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s-deployment.yaml'
    }
   
        }

    }
}
