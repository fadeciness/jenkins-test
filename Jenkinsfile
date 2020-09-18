def myVariable = 'branch'

pipeline {

    agent any

    options {
        skipDefaultCheckout()
    }

    parameters {
        string(name: 'VERSION', defaultValue: '0.0.9', description: 'Version')
        string(name: 'VERSIONSECOND', defaultValue: '0.2.9', description: 'Version')
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
                sh """echo VERSION = '${params.VERSION}' """
                sh """echo VERSION2 = '${params.VERSIONSECOND}' """
                sh 'mvn clean package install'
                //build job: 'tests', propagate: true, wait: true
            }
        }
        stage('End') {
            steps {
                sh """echo VERSION = '${params.VERSION}' """

                echo "My variable is ${myVariable}"
                script {
                    if ('12' as Integer >= 9) {
                    sh """echo 'UPPY' """
                    }


                    if (params.VERSION=='0.0.9') {
                        myVariable='one'
                        sh """echo myVariable = '${myVariable}' """
                    } else if (params.VERSION=='0.0.15') {
                        myVariable='two'
                        sh """echo myVariable = '${myVariable}' """
                    } else {
                        myVariable='three'
                        sh """echo myVariable = '${myVariable}' """
                    }
                }
                echo '========== End stage! =========='
            }
        }
        stage('Post-ENd') {
            steps {
                sh """echo myVariable = '${myVariable}' """
            }
        }
    }

}