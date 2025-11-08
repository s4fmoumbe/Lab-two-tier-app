pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                // ✅ Use plain Git URL (no markdown)
                git branch: 'main', url: 'https://github.com/s4fmoumbe/Lab-two-tier-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // ✅ Use full repository name for clarity
                    sh 'docker build -t flask-app:latest .'
                }
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                script {
                    // ✅ Safely stop and start containers
                    sh '''
                        docker compose down || true
                        docker compose up -d --build
                    '''
                }
            }
        }
    }
}
