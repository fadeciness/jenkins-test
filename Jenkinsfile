pipeline {

    agent any

    options {
        skipDefaultCheckout()
    }

    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: 'master']],
                    doGenerateSubmoduleConfigurations: false,
                    extensions: [], submoduleCfg: [],
                    userRemoteConfigs: [[
                        credentialsId: 'fadeciness',
                        url: 'https://github.com/fadeciness/jenkins-test.git'
                    ]]
                ])
            }
        }
        stage('Build') {
            steps {
                echo '========== Build stage! =========='
                sh 'ls -la'
                sh 'pwd'
                sh 'rm -rf jenkins-test || true'
                sh 'git clone https://github.com/fadeciness/jenkins-test'
                sh 'ls -la'
                sh 'pwd'
            }
        }
    }

}