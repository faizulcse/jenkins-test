node('master') {

    def IMAGE

    stage('checkout') {
        deleteDir()
        checkout scm
        echo 'Successfully checkout git repository.'
    }

    stage('docker:build') {
        IMAGE = docker.build("myubuntu/ubuntu")
        echo 'Docker build successfully done!'

    }

    stage('docker:push') {
        docker.withRegistry('https://registry.hub.docker.com','docker-hub'){
            IMAGE.push("0.1.${env.BUILD_NUMBER}")
            IMAGE.push("latest")
        }
        echo 'Successfully push docker image to dockerhub.'
    }

    stage('docker:rmi') {
        sh "docker rmi -f ${IMAGE.id}"
        sh "docker rmi -f ${IMAGE.id}:0.1.${env.BUILD_NUMBER}"
        echo 'Successfully remove docker image.'
    }
}