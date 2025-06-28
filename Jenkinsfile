pipeline {
  agent any

  stages {
    stage('Deploy to Kubernetes') {
      steps {
        sshagent(['ec2-key']) {
          sh 'scp deployment ubuntu@3.83.223.29:/tmp/deployment.yaml'
          sh 'scp service ubuntu@3.83.223.29:/tmp/service.yaml'
          sh 'ssh ubuntu@3.83.223.29 "kubectl apply -f /tmp/deployment.yaml"'
          sh 'ssh ubuntu@3.83.223.29 "kubectl apply -f /tmp/service.yaml"'
        }
      }
    }
  }
}
