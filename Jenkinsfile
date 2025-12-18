@Library('jenkins-shared-lib') _

pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Deploy using Shared Library') {
            steps {
                dockerBuildRun('nginx-html-app', 'nginx-html')
            }
        }
    }
}
