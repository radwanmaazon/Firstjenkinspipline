pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                echo 'build'
                sh "echo ${BUILD_NUMBER}"
            }
        }
    }
    stages {
    stage('test') {
            steps {
                echo 'test'
                sh """
                    echo "build number is ${BUILD_NUMBER}"
                    docker ps
                    curl --help
                """
            }
        }
    }
}