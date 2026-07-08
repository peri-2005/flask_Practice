pipeline {
    agent any

    environment {
        VENV_DIR = '.venv'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Setting up virtual environment and installing dependencies...'
                sh '''
                    python3 -m venv ${VENV_DIR}
                    . ${VENV_DIR}/bin/activate
                    pip install --upgrade pip
                    if [ -f requirements.txt ]; then
                        pip install -r requirements.txt
                    fi
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests with pytest...'
                sh '''
                    . ${VENV_DIR}/bin/activate
                    pip install pytest pytest-cov
                    pytest --junitxml=reports/result.xml
                '''
            }
            post {
                always {
                    junit 'reports/result.xml'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application to the staging environment...'
                sh '''
                    . ${VENV_DIR}/bin/activate
                    echo "Executing deployment scripts..."
                '''
            }
        }
    }

    post {
        success { echo 'Pipeline completed successfully!' }
        failure { echo 'Pipeline failed. Check the logs.' }
    }
}

