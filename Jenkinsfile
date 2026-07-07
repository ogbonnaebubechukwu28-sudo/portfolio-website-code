pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t portfolio-website .'
            }
        }

        stage('Run Application') {
            steps {
                echo 'Stopping any existing container...'
                sh 'docker stop portfolio || true'
                sh 'docker rm portfolio || true'
                echo 'Running new container...'
                sh 'docker run -d --name portfolio -p 8081:80 portfolio-website'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully! Website is running.'
        }
        failure {
            echo 'Pipeline failed. Check the logs above.'
        }
    }
}
