pipeline {
    agent any

    tools {
        nodejs 'Node22'
    }

    options {
        timestamps()
        disableConcurrentBuilds()
    }

    stages {
        stage('Verify version') {
            steps {
                sh 'node --version'
                sh 'npm --version'
            }
        }

        stage('Install') {
            steps {
                sh 'npm ci'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
                archiveArtifacts artifacts: 'dist/**', fingerprint: true
            }
        }
    }

    post {
        success { echo '✅ Pipeline exitoso' }
        failure { echo '❌ El pipeline falló' }
    }
}
