pipeline {
    agent any

    stages {
        stage('Deploy') {
            steps {
                echo "Deploying bike-showroom..."
                sh '''
                cd /var/lib/jenkins/workspace/bike-showroom
                echo "Checking port 8000..."
                PID=$(lsof -t -i:8000)
                if [ ! -z "$PID" ]; then
                    echo "Port busy, killing $PID"
                    kill -9 $PID
                fi
                echo "Starting server..."
                nohup python3 -m http.server 8000 > nohup.out 2>&1 &
                echo "Server started!"
                '''
            }
        }
    }
}

