pipeline {
    agent any

    parameters {
        string(name: 'USERNAME', defaultValue: 'John Doe', description: 'Enter your name')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Running Python script...'
                script {
                    sh "python3 app.py <<EOF\n${params.USERNAME}\nEOF"
                }
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