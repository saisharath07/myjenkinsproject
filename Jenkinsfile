pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Add your build commands here
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add your test commands here
            }
        }
        
        stage('Deploy') {
          steps {
           echo 'Deploying to EC2...'
           sh '''
           ssh -o StrictHostKeyChecking=no ubuntu@3.110.136.249 "mkdir -p ~/app"
           scp hello_world.py ubuntu@3.110.136.249:~/app/
           ssh ubuntu@3.110.136.249 "pkill -f hello_world.py || true"
           ssh ubuntu@3.110.136.249 "nohup python3 ~/app/hello_world.py &"
           '''
          }
        }
        

    }
}
