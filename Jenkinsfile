pipeline {
    agent {  label "jenkins-slave" }

      stages {
        stage('build') {
            steps {
                echo 'build'
                sh "echo ${BUILD_NUMBER}"
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