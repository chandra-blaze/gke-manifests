pipeline {
    agent any
    environment {
        PROJECT_ID = 'prj-snapmint-dev'
        CLUSTER_NAME = 'gke-snapmint-dev-zonal-as'
        LOCATION = 'asia-south1-a'
        CREDENTIALS_ID = 'prj-snapmint-commonservices'
    }
    stages {
        stage("Checkout code") {
            steps {
                checkout main
            }
        }
        
        stage('Deploy to GKE') {
            steps{
                //sh "sed -i 's/hello:latest/hello:${env.BUILD_ID}/g' deployment.yaml"
                step([$class: 'KubernetesEngineBuilder', projectId: env.PROJECT_ID, clusterName: env.CLUSTER_NAME, location: env.LOCATION, manifestPattern: '*.yaml', credentialsId: env.CREDENTIALS_ID, verifyDeployments: true])
            }
        }
    }    
}
