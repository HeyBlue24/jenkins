pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/HeyBlue24/jenkins.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Assuming a Node.js project. Adjust according to your project's dependencies
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                // Run your test script. Adjust according to your project's test command
                sh 'npm test'
            }
        }

        stage('Code Check') {
            steps {
                // Perform code check. Assuming eslint for a Node.js project
                sh 'npm run lint'
            }
        }
    }

    post {
        always {
            // Archive test results and other reports
            junit '**/test-results.xml'
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
        }
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
