node {
    stage ("clean") {
        cleanWs()
    }
    stage ("clone") {
        git branch: 'main', url: 'https://github.com/ArunMagi/sample-spring-boot-java-docker-application.git'
    }
    stage ("build"){
        sh "mvn clean install"
    }
    stage ("docker-image") {
        sh "docker build -t test-app ."
    }
    stage ("docker-container"){
        sh "docker run -d --name test-app -p 8084:8080 test-app"
    }
}
