pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo Building project...'
            }
        }
        stage('Test') {
            steps {
                sh 'echo Running test on the project...'
            }
        }
        stage('Meterian Scan') {
            steps {
                withCredentials([string(credentialsId: 'meterianApiToken', variable: 'METERIAN_API_TOKEN_MTA')]) {
                    sh 'echo Perform Meterian vulnerability scan...'
                    sh 'docker run --rm -v $(pwd):/workspace -e METERIAN_API_TOKEN=$METERIAN_API_TOKEN_MTA meterian/cli' 
                }
            }
        }
        stage("Deploy") {
            steps {
                sh 'echo Successful deployed!'
            }
        }
    }
}