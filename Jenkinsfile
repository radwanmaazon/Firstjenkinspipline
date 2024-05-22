pipeline {
    agent  {  label "flask-slave" }
    parameters {
        choice (name: 'ENV' , choices: ['dev', 'test', 'prod', 'release'])
    }
    stages {
        stage('build') {
            steps {
                echo 'build'
                script {
                    if (params.ENV == 'release'){
                        withCredentials([usernamePassword(credentialsId: 'radwandocker-ID', passwordVariable: 'dockerpass', usernameVariable: 'dockeruser')]) {
                        sh """
                            docker build -t  radwanmaazon/coffeewebsite:${BUILD_NUMBER} .
                            docker login -u ${dockeruser} -p ${dockerpass}
                            docker push radwanmaazon/coffeewebsite:${BUILD_NUMBER}
                            echo ${BUILD_NUMBER} > ../coffeewebsite-build_number.txt
                        """
                        }
                    }
                }
            }
        } 

        stage('deploy') {
            steps {
                echo 'deploy'
                script {
                    if (params.ENV == 'test'|| params.ENV == 'dev'|| params.ENV == 'prod'){
                        withCredentials([file(credentialsId: 'kubernates-ID', variable: 'KUBECONFIG')]) { 
                            sh """
                                export BUILD_NUMBER=\$(cat ../coffeewebsite-build_number.txt)
                                cp Deployment/deployjenkins.yml Deployment/deployjenkins.yml.tmp
                                cat Deployment/deployjenkins.yml.tmp | envsubst > Deployment/deployjenkins.yml
                                rm Deployment/deployjenkins.yml.tmp
                                kubectl apply -f Deployment  
                                
                                # echo ${KUBECONFIG}
                            """                
                        }
                    }
                }
            }
        }
    }
}
