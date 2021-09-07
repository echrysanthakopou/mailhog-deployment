pipeline {
    agent any
    stages {
        stage ('Stage 1 - Checkout Code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']],
                    doGenerateSubmoduleConfigurations: false, extensions: [],
                    submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'e69ff7f5-1d77-48c6-9f2c-b2123caac355',
                    url: 'https://github.com/echrysanthakopou/mailhog-deployment.git']]])
            }
        }
        stage('Stage 2 - Deploy Mailhog') {
            steps {
                sh('microk8s kubectl apply -f ./k8s')
            }
        }
    }
}
