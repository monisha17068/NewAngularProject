pipeline {
    agent any
   

    stages {
        stage('git') {
            steps {
               git branch: 'main', credentialsId: '28a05ef9-3b3c-4466-847a-0a6a0edce8b5', url: 'https://github.com/monisha17068/NewAngularProject.git'
            }
        }
        stage('sonar') 
          {
    
       steps {
   
     

sh '$SCANNER_HOME/opt/sonar-scanner/bin/sonar-scanner -Dsonar.projectKey=angular_scanner -Dsonar.sources=. '
}
}
    stage('build') {
            steps {
                
               sh 'npm install'
               sh 'ng build --prod'
               
            }
        }    
  }
   
    }



