pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage ('build') {
            steps {
                echo 'Building app...'
                sh 'mvn -B clean package'
                echo 'Building succeded!'
            }
        }

        stage('test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }

        stage('Deliver') {
            steps {
                sh 'chmod +x ./jenkins/delivery.sh'
                // sh './jenkins/delivery.sh'
            }
        }
    }
}