pipeline {

    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: 'master'],
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
            echo '========== Build stage! =========='
            ls -la
        }
    }

}