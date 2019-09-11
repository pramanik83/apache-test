node {
    def apachedocker

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        apachedocker = docker.build("pramanik83/apache-test")
    }

    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            apachedocker.push("${env.BUILD_NUMBER}")
            apachedocker.push("latest")
        }
    }
}
