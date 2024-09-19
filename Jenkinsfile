pipeline {
    agent any
    environment {
        // Define environment variables
        IMAGE_NAME = 'dasnarayanb2/restapp'
        PORT_MAPPING = '9090:8080'
        CONTAINER_NAME = 'ajay'
        TAG = "${BUILD_NUMBER}"
    }
    
    stages {
        
        stage('git-clone') {
            steps {
                sh 'https://github.com/dreamkiller67/RestApp.git'
            }
        }
 
        
        stage('mvn-package') {
            steps {
               sh 'mvn package' //*** this is not working for me***//
              // sh 'mvn install:install-file "-Dfile=app.jar" "-DgroupId=com.restapp" "-DartifactId=restapp" "-Dversion=0.0.1-SNAPSHOT" "-Dpackaging=jar" "-DgeneratePom=true"'
            }
        }
        
        stage('image-creation') {
            steps {
                sh 'docker build -t $IMAGE_NAME -f Dockerfile .'
            }
        }
        
        stage('image-upload') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'password', usernameVariable: 'username')]) {
                sh "docker login -u ${username} -p ${password}"
                sh "docker push $IMAGE_NAME:${BUILD_NUMBER}"
                }
                }
        }
        
        // Deploy stage starts here
        stage('Deploy') {
            steps {
                // Deploy the Docker image to your environment (e.g., Kubernetes, Docker Swarm)
                sh '''if [ "$(docker ps -aq -f name=$CONTAINER_NAME)" ]; then
                         echo "Stopping and removing existing container..."
                         docker stop $CONTAINER_NAME
                         docker rm $CONTAINER_NAME
                   fi'''
                sh 'docker run -d -p 9090:8080 --name $CONTAINER_NAME $IMAGE_NAME:${BUILD_NUMBER}'
            }
        }
     // Deploy stage ends here
        
        
    }
}

