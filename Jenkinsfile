pipeline {
    agent any
    stages{
        stage ("clone") {
            steps {
                git branch: 'main', url: 'https://github.com/ArunMagi/sample-java-spring-app.git'
            }
        }
        stage ("build") {
            steps {
                sh "mvn clean install"
            }
        }
        stage ("docker image"){
            steps {
                sh "docker build -t arunmagi/java ."
                sh "docker images"
            }
        }
        stage("docker hub") {
            steps {
                sh "docker login -u arunmagi -p Arun@ak@99"
                sh "docker push arunmagi/java"
            }
        }
        stage ("docker conatainer"){
            steps {
                sh "docker rm -f java"
                sh "docker run -d --name java -p 8087:8080 arunmagi/java"
            }
        }
    }
}
