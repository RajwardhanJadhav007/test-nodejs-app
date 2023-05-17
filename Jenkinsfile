pipeline { 
  
   agent any

   stages {
   
     stage('Install Dependencies') { 
        steps { 
           sh 'npm install' 
        }
     }
     
     stage('Test') { 
        steps { 
           sh 'echo "testing application..."'
        }
     }

     stage("Deploy application") { 
         steps { 
           sh 'echo "deploying application..."'
         }
     }
     
     stage('Build Docker Image') {
        steps {
            script {
                sh 'docker build -t rajwardhan007/mynodejsapp-1.0 .'
            }
        }
     }
     
     stage("Push Docker image") {
        steps {
            script {
                withCredentials([string(credentialsId: 'rajwardhan007', variable: 'dockerhubpwd')]) {
                    sh "docker login -u rajwardhan007 -p ${dockerhubpwd}"
                }
                sh "docker push rajwardhan007/mynodejsapp-1.0"
            }
        }
     }
     
     stage('Run Docker Container') {
        steps {
            sh 'docker run -d --name mynodejsapp -p 8888:8888 rajwardhan007/mynodejsapp-1.0'
        }
     }
   }

}
