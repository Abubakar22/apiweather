pipeline {
    agent any

    stages {
        stage ('Build Docker Image') {
            steps {
                
                    sh 'Docker build -t us.gcr.io/api/apiweather:0.1'
            }
        }

        stage ('Push Docker Image to GCR') {
            steps{
                    
                    sh 'sudo docker push us.gcr.io/api/apiweather:0.1'
                    echo "Image to push is us.gcr.io/api/apiweather:0.1"
            }
        
        }
		
		stage ('Deploying microservice to Kubernetes') {
			steps{
					sh 'kubectl apply -f deployment.yml'
					sh 'kubectl apply -f service.yml'
					
			}
			
		}
		
	}
	
}