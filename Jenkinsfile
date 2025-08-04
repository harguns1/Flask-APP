pipeline {
  agent any

  stages {
    stage('Deploy to Kubernetes') {
      steps {
        sshagent(['ec2-key']) {
          sh 'scp -o StrictHostKeyChecking=no deployment.yaml ubuntu@13.221.87.178:/tmp/deployment.yaml'
          sh 'scp -o StrictHostKeyChecking=no service.yaml ubuntu@13.221.87.178:/tmp/service.yaml'
          sh 'ssh -o StrictHostKeyChecking=no ubuntu@13.221.87.178 "kubectl apply -f /tmp/deployment.yaml --validate=false"'
          sh 'ssh -o StrictHostKeyChecking=no ubuntu@13.221.87.178 "kubectl apply -f /tmp/service.yaml --validate=false"'
        }
      }
    }
  }
}
