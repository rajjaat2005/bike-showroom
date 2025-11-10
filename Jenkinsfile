pipeline {
    agent any

    stages {
        stage('Deploy') {
            steps {
                echo "🚀 Deploying bike-showroom project..."
                sh '''
                cd $WORKSPACE
                echo "✅ Checking port 8001..."
                PID=$(lsof -t -i:8001)
                if [ ! -z "$PID" ]; then
                    echo "⚠️ Port busy, killing old process..."
                    kill -9 $PID
                fi
                echo "🚀 Starting server..."
                nohup python3 -m http.server 8001 &
                echo "✅ Deployment successful!"
                '''
            }
        }
    }
}


