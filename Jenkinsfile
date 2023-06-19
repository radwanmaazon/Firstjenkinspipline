pipeline {
    agent {  label "jenkins-slave" }

      stages {
        stage('build') {
            steps {
                echo 'build'
                 withCredentials([usernamePassword(credentialsId: 'radwandocker-ID', passwordVariable: 'dockerpass', usernameVariable: 'dockeruser')]) {
                sh """
                    docker build -t  radwanmaazon/coffeewebsite .
                    docker login -u ${dockeruser} -p ${dockerpass}
                    docker push radwanmaazon/coffeewebsite
                """
            }
        }
        stage('deploy') {
            steps {
                echo 'deploy'
                sh """
                    echo "build number is ${BUILD_NUMBER}"
                    docker ps
                    curl --help
                """
            }
        }
    }
}