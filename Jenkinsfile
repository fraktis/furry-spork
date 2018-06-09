pipeline {
    agent { docker { image 'python:3.5.1' } }
     stages {
        stage('Build') {
            steps {
                echo 'Building'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
            }
        }
        stage('Deploy - smoketest') {
            steps {
                sh './deploy-st'
                sh './run-smoke-tests'
            }
        }
        stage('Deploy staging') {
            steps {
                echo 'Deploying to staging'
                sh '/deploy-staging'
            }
        }
        stage('Sanity check') {
            steps {
                input "Does the staging environment look ok?"
            }
        }
        stage('Deploy - Production') {
            steps {
                sh './deploy-production'
            }
        }
    }
}
