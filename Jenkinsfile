pipeline {
  agent any

  stages {
    stage('Deploy to Kubernetes') {
      steps {
        sshagent(['ec2-key']) {
          sh 'scp k8s/deployment.yaml ubuntu@3.83.223.29:/tmp/'
          sh 'scp k8s/service.yaml ubuntu@3.83.223.29:/tmp/'
          sh 'ssh ubuntu@3.83.223.29 "kubectl apply -f /tmp/deployment.yaml"'
          sh 'ssh ubuntu@3.83.223.29 "kubectl apply -f /tmp/service.yaml"'
        }
      }
    }
  }
}
