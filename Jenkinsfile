pipeline {
    agent { 
        node {
            label 'new'
            }
      }
    
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                pip install --no-cache-dir -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                python3 app.py 
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}
