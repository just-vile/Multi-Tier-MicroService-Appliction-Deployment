pipeline {
    agent any
    environment{
        SCANNER_HOME= tool 'sonar-scanner'
    }
    stages {
        stage('git checkout') {
            steps {
                git branch: 'latest', url: 'https://github.com/just-vile/Multi-Tier-MicroService-Appliction-Deployment.git'
            }
        }
        stage('SonarQube') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh ''' 
                    $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=10-Tier -Dsonar.ProjectName=10-Tier -Dsonar.java.binaries=. 
                    '''   
                }
                    
            }
                
        }
        stage('adservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/adservice') {
                            sh 'docker build -t levi2708/adservice:latest .'
                            sh "docker push levi2708/adservice:latest"
                            sh "docker rmi levi2708/adservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('cartservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/cartservice/src/') {
                            sh 'docker build -t levi2708/cartservice:latest .'
                            sh "docker push levi2708/cartservice:latest"
                            sh "docker rmi levi2708/cartservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('checkoutservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/checkoutservice/') {
                            sh 'docker build -t levi2708/checkoutservice:latest .'
                            sh "docker push levi2708/checkoutservice:latest"
                            sh "docker rmi levi2708/checkoutservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('currencyservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/currencyservice/') {
                            sh 'docker build -t levi2708/currencyservice:latest .'
                            sh "docker push levi2708/currencyservice:latest"
                            sh "docker rmi levi2708/currencyservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('emailservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/emailservice/') {
                            sh 'docker build -t levi2708/emailservice:latest .'
                            sh "docker push levi2708/emailservice:latest"
                            sh "docker rmi levi2708/emailservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('frontend'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/frontend/') {
                            sh 'docker build -t levi2708/frontend:latest .'
                            sh "docker push levi2708/frontend:latest"
                            sh "docker rmi levi2708/frontend:latest"
                        }
                    }
            }
            }
        }
    
        stage('loadgenerator'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/loadgenerator/') {
                            sh 'docker build -t levi2708/loadgenerator:latest .'
                            sh "docker push levi2708/loadgenerator:latest"
                            sh "docker rmi levi2708/loadgenerator:latest"
                        }
                    }
            }
            }
        }
    
        stage('paymentservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/paymentservice/') {
                            sh 'docker build -t levi2708/paymentservice:latest .'
                            sh "docker push levi2708/paymentservice:latest"
                            sh "docker rmi levi2708/paymentservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('productcatalogservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/productcatalogservice/') {
                            sh 'docker build -t levi2708/productcatalogservice:latest .'
                            sh "docker push levi2708/productcatalogservice:latest"
                            sh "docker rmi levi2708/productcatalogservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('recommendationservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/recommendationservice/') {
                            sh 'docker build -t levi2708/recommendationservice:latest .'
                            sh "docker push levi2708/recommendationservice:latest"
                            sh "docker rmi levi2708/recommendationservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('shippingservice'){
            steps{
             script{
              withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/10-Tier/src/shippingservice/') {
                            sh 'docker build -t levi2708/shippingservice:latest .'
                            sh "docker push levi2708/shippingservice:latest"
                            sh "docker rmi levi2708/shippingservice:latest"
                        }
                    }
            }
            }
        }
        
        stage('K8-Deploy'){
            steps{
                withKubeConfig(caCertificate: '', clusterName: 'my-eks2', contextName: '', credentialsId: 'k8s-token-webapps', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://67FBD3D51BE6C68A23FDA36D74A5892D.gr7.us-east-1.eks.amazonaws.com') {
                    sh 'kubectl apply -f deployment-service.yml'
                    sh 'kubectl get pods'
                    sh 'kubectl get svc'
                }
            }
        }
}
}


