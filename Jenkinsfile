pipeline{
agent any
  stages{
    stage("Buid"){
      steps{
       sh '/home/younouss/maven3.6/bin/mvn clean install'
      }
    }
    
    stage("test"){
      steps{
         junit 'reports/**/*.xml'
      }
    }
  }
}
