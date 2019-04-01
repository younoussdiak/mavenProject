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
    text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
    booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
    password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    
  }
  
  stages{
    stage("Buid"){
      steps{
       sh '/home/younouss/maven3.6/bin/mvn clean install'
      }
    }
      stage("VARIABLES ENV"){
      steps{
       sh 'echo ${color}'
       sh "echo ${env.BRANCH_NAME}"
      }
    }
      stage("PARAMETTRES"){
        steps{
           echo "Hello ${params.PERSON}"
           echo "Choice: ${params.CHOICE}"
           echo "Biography: ${params.BIOGRAPHY}"
           echo "Toggle: ${params.TOGGLE}"
           echo "Password: ${params.PASSWORD}"
    
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
