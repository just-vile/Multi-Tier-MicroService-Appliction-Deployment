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

                            sh '''
                            trivy image levi2708/adservice:latest > trivy_adservice_report.txt || true
                            cat trivy_adservice_report.txt
                            '''

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

                            sh '''
                            trivy image levi2708/carservice:latest > trivy_carservice_report.txt || true
                            cat trivy_carservice_report.txt
                            '''

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

                            sh '''
                            trivy image levi2708/checkoutservice:latest > trivy_checkoutservice_report.txt || true
                            cat trivy_checkoutservice_report.txt
                            '''

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

                            sh '''
                            trivy image levi2708/currencyservice:latest > trivy_currencyservice_report.txt || true
                            cat trivy_currencyservice_report.txt
                            '''

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
                            sh '''
                            trivy image levi2708/emailservice:latest > trivy_emailservice_report.txt || true
                            cat trivy_emailservice_report.txt
                            '''

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

                            sh '''
                            trivy image levi2708/frontend:latest > trivy_frontend_report.txt || true
                            cat trivy_frontend_report.txt
                            '''

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

                            sh '''
                            trivy image levi2708/loadgenerator:latest > trivy_loadgenerator_report.txt || true
                            cat trivy_loadgenerator_report.txt
                            '''

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

                            sh '''
                            trivy image levi2708/paymentservice:latest > trivy_paymentservice_report.txt || true
                            cat trivy_paymentservice_report.txt
                            '''

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

                            sh '''
                            trivy image levi2708/productcatalogservice:latest > trivy_productcatalogservice_report.txt || true
                            cat trivy_productcatalogservice_report.txt
                            '''

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

                            sh '''
                            trivy image levi2708/recommendationservice:latest > trivy_recommendationservice_report.txt || true
                            cat trivy_recommendationservice_report.txt
                            '''

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

                            sh '''
                            trivy image levi2708/shippingservice:latest > trivy_shippingservice_report.txt || true
                            cat trivy_shippingservice_report.txt
                            '''

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


