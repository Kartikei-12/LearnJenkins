pipeline {
    agent { docker { image 'python:3.12.1-alpine3.19' } }
    stages {
        stage('Build') {
            steps {
                retry (2) {
                    sh 'python --version'
                    sh 'ls -all'
                    sh 'python main.py'
                }
                timeout(time: 1, unit: 'MINUTES') {
                    echo 'TIMEOUT failure'
                }
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
