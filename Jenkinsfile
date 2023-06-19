pipeline {
    agent {  label "jenkins-slave" }

    stages {
        stage('build') {
            steps {
                echo 'build'
                withCredentials([usernamePassword(credentialsId: 'radwandocker-ID', passwordVariable: 'dockerpass', usernameVariable: 'dockeruser')]) {
                sh """
                    docker build -t  radwanmaazon/coffeewebsite:${BUILD_NUMBER} .
                    docker login -u ${dockeruser} -p ${dockerpass}
                    # docker push radwanmaazon/coffeewebsite:${BUILD_NUMBER}
                """
                }
            }
        }
        stage('deploy') {
            steps {
                echo 'deploy'
                sh """
                    cp Deployment/deployment.yml Deployment/deployment.yml.tmp
                    cat Deployment/deployment.yml.tmp | envsubst > Deployment/deployment.yml
                    cat Deployment/deployment.yml
                """
            }
        }
    }
}
