pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Running Python script...'
                sh 'python app.py'
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}