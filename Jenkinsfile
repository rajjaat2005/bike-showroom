stage('Deploy') {
  steps {
    sh '''
    set -euo pipefail
    echo "🔍 Checking port 8001..."
    PID=$(lsof -t -i:8001 || true)
    if [ -n "$PID" ]; then
      echo "🛑 Stopping existing process on port 8001 (PID: $PID)"
      kill -9 $PID || true
      sleep 1
    else
      echo "✅ No existing process found on port 8001"
    fi

    echo "🚀 Starting Django server..."
    nohup python3 manage.py runserver 0.0.0.0:8001 > server.log 2>&1 &
    sleep 3
    ss -ltnp | grep 8001 || echo "⚠️ Server might not have started"
    echo "✅ Deploy stage completed successfully"
    '''
  }
}

