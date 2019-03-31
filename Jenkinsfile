pipeline{
agent any
  tools {
    maven 'maven3'
}
  stages{
    stage("Buid"){
      steps{
       sh '/home/younouss/maven3.6/bin/mvn clean install'
      }
      post {
        success {
            junit 'target/surefire-reports/**/*.xml' 
        }
     }
    }
    
    stage("test"){
      steps{
          junit 'target/surefire-reports/**/*.xml'
      }
    }
  }
}
