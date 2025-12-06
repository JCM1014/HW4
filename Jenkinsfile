pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                // Clone the GitHub repo
                checkout scm
            }
        }

         stage('Install Dependencies') {
            steps {
                nodejs(nodeJSInstallationName: 'NodeJS 18') {
                    sh 'npm install'
                }
            }
        }
        stage('Build') {
            steps {
                nodejs(nodeJSInstallationName: 'NodeJS 18') {
                    sh 'npm run build'
                }
            }
        }
        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'build/**', fingerprint: true
            }
        }
    }
}