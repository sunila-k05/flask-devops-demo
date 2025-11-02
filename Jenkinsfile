pipeline {
  agent any

  stages {
    stage('Clone Repository') {
      steps {
        git 'https://github.com/sunila-k05/flask-devops-demo.git'
      }
    }

    stage('Build Environment') {
      steps {
        sh '''
        python3 -m venv venv
        source venv/bin/activate
        pip install -r requirements.txt
        '''
      }
    }

    stage('Deploy Application') {
      steps {
        sh '''
        # Stop old process if running
        sudo pkill -f app.py || true

        # Start Flask app in background
        nohup python3 app.py > flask.log 2>&1 &

        echo "✅ Flask app deployed successfully!"
        '''
      }
    }
  }
}
