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
                    #docker push radwanmaazon/coffeewebsite:${BUILD_NUMBER}
                """
                }
            }
        }
        stage('deploy') {
            steps {
                echo 'deploy'
                withCredentials([file(credentialsId: 'kubernates-ID', variable: 'KUBECONFIG')]) { 
                sh """
                    cp Deployment/deployjenkins.yml Deployment/deployjenkins.yml.tmp
                    cat Deployment/deployjenkins.yml.tmp | envsubst > Deployment/deployjenkins.yml
                    rm Deployment/deployjenkins.yml.tmp
                     
                """                
                }
            }
        }
    }
}
