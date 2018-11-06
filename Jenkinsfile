pipeline {
 agent any
 stages {
        stage('Build') {
            steps {
                echo 'Building'
                        }
        }
                stage('Build Docker Image'){
                steps {
                            sh 'docker build -t sangana/new-nginx:${BUILD_NUMBER} .'
                }
                }
        stage ('test'){
                steps {
                        echo 'testing'
                        }
            }
        stage('Push Docker Image'){
                     steps {
                             withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]) {
                                        sh "docker login -u sangana -p ${dockerHubPwd}"
                        sh 'docker push sangana/new-nginx:${BUILD_NUMBER}'
                }
                        }
        }
    }
}


