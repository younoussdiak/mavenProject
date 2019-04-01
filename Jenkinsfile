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
    buildDiscarder(logRotator(numToKeepStr: '3')) 
    //Interdit les exécutions simultanées du pipeline (Peut être utile pour empêcher les accès simultanés aux ressources partagées)
     disableConcurrentBuilds() 
  }
  parameters { 
    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
     choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    
  }
  
  stages{
    stage("Buid"){
      steps{
       sh '/home/younouss/maven3.6/bin/mvn clean install'
      }
    }
      stage("varible ENV"){
      steps{
       sh 'echo ${color}'
       sh "echo ${env.BRANCH_NAME}"
      }
    }
      stage("PARAMETTRES"){
        steps{
           echo "Hello ${params.PERSON}"
           echo "Choice: ${params.CHOICE}"
    
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
