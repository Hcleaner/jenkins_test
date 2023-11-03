pipeline {
    agent any

    parameters {
        string(name: 'USERNAME', defaultValue: 'John Doe', description: 'Enter your name')
    }

    stages {
        stage('Setup') {
            steps {
                script {
                    // If venv directory doesn't exist, create it and install dependencies
                    sh '[ -d venv ] || { python3 -m venv venv && source venv/bin/activate && pip install -r requirements.txt; }'
                    // Activate the virtual environment
                    sh 'source venv/bin/activate'
                }
            }
        }

        stage('Build') {
            steps {
                echo 'Running Python script...'
                script {
                    // Execute your Python script within the virtual environment
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