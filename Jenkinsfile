pipeline{
  agent any

  stages{
    stage('Build Docker Image'){
      steps{
        script{
          dockerapp = docker.Build("caiogrigoleto/kube-news:${env.BUILD_ID}",'-f ./src/Dockerfile ./src')
        }
      }
    }
  }
}