pipeline{
agent any
  tools {
    maven 'maven3'
}
  environment {
      BRANCH_NAME = 'AVIRONNEMT VARIABLE'
       color = "blue"
  }
  options { 
    //Conservez les artefacts et la sortie de la console pour le nombre spécifique d’exécutions récentes du pipeline.
    buildDiscarder(logRotator(numToKeepStr: '1')) 
    //Interdit les exécutions simultanées du pipeline (Peut être utile pour empêcher les accès simultanés aux ressources partagées)
     disableConcurrentBuilds() 
  }
  
  stages{
    stage("Buid"){
      steps{
       sh '/home/younouss/maven3.6/bin/mvn clean install'
       sh 'echo ${color}'
       sh "echo ${env.BRANCH_NAME}"
      
      }
     
    }
  }
  
   post {
        success {
            junit 'target/surefire-reports/**/*.xml' 
        }
        failure {
            echo 'LE JOB A ECHOUE'
        }
     }
}
