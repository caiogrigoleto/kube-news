pipeline{
  agent any

  stages{


    stage('Build Docker Image'){
      steps{
        script{
          dockerapp = docker.build("caiogrigoleto/kube-news:${env.BUILD_ID }",'-f ./src/Dockerfile ./src')
        }
      }
    }


    stage('Push Docker Image'){
      steps{
        script{
          docker.withRegistry('https://registry.hub.docker.com', 'dockerhub'){
            dockerapp.push("latest")
            dockerapp.push("${env.BUILD_ID}")
            
          }
        }
      }
    }

    stage('Deploy Kubernetes Image'){
      steps{
        withKubeconfig([credencialsId: 'kubeconfig']){
          sh 'kubectl apply -f ./Deplymentt.yaml'
        }
      }
    }
    
  }
}