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
     timeout(time: 1, unit: 'HOURS')
  }
  parameters { 
    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
    choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
    booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
    password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    
  }
  
  stages{
    stage("BUILD"){
      steps{
       sh '/home/younouss/maven3.6/bin/mvn clean install'
      }
    }
    stage("RELEASE"){
      steps{
       sh '/home/younouss/maven3.6/bin/mvn release:prepare'
      }
}
    stage('Publish Result') {
      steps {  
        echo 'Testing..'      
        archiveArtifacts '**/*.war,**/*.jar'
      }
    }
    stage('DEPLOY') {
        input {
            message "Do you want to deploy?"
            ok "Yes."
        }
        steps {
            echo "Deploying ..."
            sh 'cp target/*.jar /home/younouss/RepArtifact'
        }
    }

   stage("VARIABLES ENV"){
      steps{
       sh 'echo ${color}'
       sh "echo ${env.BRANCH_NAME}"
      }
    }
   stage("PARAMETTRES"){
        input {
            message "afficher les varibles?"
            ok "Yes"
            //submitter "alice,bob"
        }
        steps{
           echo "Hello ${params.PERSON}"
           echo "Choice: ${params.CHOICE}"
           echo "Biography: ${params.BIOGRAPHY}"
           echo "Toggle: ${params.TOGGLE}"
           echo "Password: ${params.PASSWORD}"
           //mail to: 'younouss.diakite@gmail.com',
           //subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
           //body: "Something is wrong with ${env.BUILD_URL}"
      }
    }
  }
  
   post {
        success {
            junit 'target/surefire-reports/**/*.xml' 
           // mail bcc: '', body: 'SUCCESS', cc: '', from: '', replyTo: '', subject: 'Build failed', to: 'younouss.diakite@gmail.com'
        }
        failure {
            echo 'LE JOB A ECHOUE'
        }
     }
}
