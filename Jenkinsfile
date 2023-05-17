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
  
   }

}
