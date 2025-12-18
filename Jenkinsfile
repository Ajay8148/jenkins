pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Build step - static HTML project'
                sh 'ls -l'
            }
        }

        stage('Test') {
            steps {
                echo 'Running basic tests'
                sh '''
                test -f index.html
                test -f about.html
                '''
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building Docker image'
                sh 'docker build -t nginx-html-app .'
            }
        }

        stage('Run Container') {
            steps {
                echo 'Running Docker container'
                sh '''
                docker rm -f nginx-html || true
                docker run -d -p 8082:80 --name nginx-html nginx-html-app
                '''
            }
        }
    }
}
