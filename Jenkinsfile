pipeline{
agent any
  tools {
    maven 'maven3'
}
  environment {
      BRANCH_NAME = 'MESTARISATION'
       color = "blue"
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
