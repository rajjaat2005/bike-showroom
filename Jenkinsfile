stage('Deploy') {
    steps {
        echo "🚀 Deploying bike-showroom project..."
        sh '''
        cd /var/lib/jenkins/workspace/bike-showroom
        echo ✅ Checking port 8000...
        PID=$(lsof -t -i:8000)
        if [ ! -z "$PID" ]; then
            echo "🛑 Port 8000 busy, killing process $PID"
            kill -9 $PID
        fi

        echo "▶️ Starting server on port 8000..."
        nohup python3 -m http.server 8000 > nohup.out 2>&1 &
        echo "✅ Server started successfully!"
        '''
    }
}

