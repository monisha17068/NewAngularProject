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
        
         stage('docker') {
            steps {
                
               sh 'docker build -t Angular:1.1 .'
               sh 'docker run -d -p 8084:80 Angular:1.1'
       
}
}
}
 post {
        always {
            
            
            emailext body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}",
                recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
                subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
            
        }
   
  }
   
    }



