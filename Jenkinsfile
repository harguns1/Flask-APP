pipeline {
  agent any

  stages {
    stage('Deploy to Kubernetes') {
      steps {
        sshagent(['ec2-key']) {
          sh 'scp -o StrictHostKeyChecking=no deployment.yaml ubuntu@3.83.223.29:/tmp/deployment.yaml'
          sh 'scp -o StrictHostKeyChecking=no service.yaml ubuntu@3.83.223.29:/tmp/service.yaml'
          sh 'ssh -o StrictHostKeyChecking=no ubuntu@3.83.223.29 "kubectl apply -f /tmp/deployment.yaml"'
          sh 'ssh -o StrictHostKeyChecking=no ubuntu@3.83.223.29 "kubectl apply -f /tmp/service.yaml"'
        }
      }
    }
  }
}
