pipeline {
    agent any
    environment {
        DOCKER_HUB_REPO = "mikehj24/miko_flask_app"
        CONTAINER_NAME = "miko_flask_app"
        STUB_VALUE = "200"
        REGISTRY_CREDENTIAL = "dockerhub"
    } 
    

    stages {
        
        stage('Build') {
            steps {
                    //  Building new image
                    sh 'rm -rf mikoflaskapp-latest'
                    sh 'git clone https://github.com/mikehj122498/mikoflaskapp-latest.git'
		    sh 'cd mikoflaskapp-latest'                   
                    // create new Docker repo image
                    sh 'docker build -t mikehj24/mikoflaskapp-latest .'
                }
        }
                
        stage('Publish'){
            steps{
                //  Pushing Image to Repository
                	sh 'docker push mikehj24/mikoflaskapp-latest'                              
                	echo "Image built and pushed to repository"
            }
        }
        
        
        stage('Fastest of Foxes') {
            steps {
                script{
                     sh 'python web.py'
                }
            }
        }
    }
}
