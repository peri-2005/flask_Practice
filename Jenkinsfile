# This is again a test after adding node and node got connected from Jenkins
# This is to test the script execution
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

    #post {
    #    success { echo 'Pipeline completed successfully!' }
    #    failure { echo 'Pipeline failed. Check the logs.' }
    #}
     post {
        success {
            emailext (
                subject: "SUCCESSFUL: Job '${env.JOB_NAME}' [Build #${env.BUILD_NUMBER}]",
                body: """<p>The build completed successfully.</p>
                       <p><strong>Job:</strong> ${env.JOB_NAME}<br/>
                       <strong>Build:</strong> #${env.BUILD_NUMBER}<br/>
                       <strong>URL:</strong> <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>""",
                to: 'aparna.alapana@gmail.com',
                mimeType: 'text/html'
            )
        }
        
        failure {
            emailext (
                subject: "FAILED: Job '${env.JOB_NAME}' [Build #${env.BUILD_NUMBER}]",
                body: """<p>The build has failed. Please check the logs immediately.</p>
                       <p><strong>Job:</strong> ${env.JOB_NAME}<br/>
                       <strong>Build:</strong> #${env.BUILD_NUMBER}<br/>
                       <strong>Console Logs:</strong> <a href="${env.BUILD_URL}console">${env.BUILD_URL}console</a></p>""",
                to: 'aparna.alapana@gmail.com',
                mimeType: 'text/html'
            )
        }
    } 
}

