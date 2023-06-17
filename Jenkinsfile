pipeline {
    agent any 
    stages {
        stage ('cleaning') {
            steps {
                cleanWs()
            }
        }
        stage  ("cloning"){
            steps{
                git branch: 'main', url: 'https://github.com/ArunMagi/sample-spring-boot-java-docker-application.git'
                sh 'ls -l'
            }
        }
        stage ('complile') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage ('contaization') {
            steps {
                sh 'docker build -t app .'
                sh 'docker images'
            }
        }
        stage ('save the image') {
            steps {
                sh 'docker login -u arunmagi -p Arun@ak@99'
                sh 'docker tag app arunmagi/app'
                sh 'docker push arunmagi/app'
            }
        }
        stage ('run the container') {
            steps {
                sh 'docker rm -f app'
                sh 'docker run -d  --name app -p 8082:8080 arunmagi/app'
            }
        }
        stage
    }
}
