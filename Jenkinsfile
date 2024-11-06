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
