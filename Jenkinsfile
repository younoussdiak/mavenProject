pipeline{
agent any
  stages{
    stage("Buid"){
      steps{
       sh '/home/younouss/maven3.6/bin/mvn clean package'
      }
    }
    
    stage("test"){
      steps{
        sh '/home/younouss/maven3.6/bin/mvn test'
      }
    }
  }
}
