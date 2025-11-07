pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/rajjaat2005/bike-showroom.git'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                PID=$(lsof -t -i:8001)
                if [ ! -z "$PID" ]; then
                    kill -9 $PID
                fi
                nohup python3 -m http.server 8001 --bind 0.0.0.0 &
                '''
            }
        }
    }

    post {
        success {
            echo "Deployment completed successfully!"
        }
        failure {
            echo "Deployment failed!"
        }
    }
}
