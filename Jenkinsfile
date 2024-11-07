pipeline {
    agent any
    environment {
        DOCKER_LOGIN=credentials('DOCKER_LOGIN')
    }
    stages {
        stage('Docker Login') {
            steps {
                sh 'docker login -u ${DOCKER_LOGIN_USR} -p ${DOCKER_LOGIN_PSW}'
            }
        }
        stage('Jenkins ssh') {
            steps {
                sh 'ssh jenkins@35.233.72.76 touch finalfile.txt'
            }
        }
        stage('SonarQube Analysis') {
            environment {
                scannerHome = tool 'sonarqube'
            }
            steps {
                withSonarQubeEnv('sonar-qube-1') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        } 
    }
}
