pipeline{
agent any
tools{
maven'MAVEN_HOME'
    }
stages{
 stage('checkout source code'){
   steps{
      git 'https://github.com/Kavanapc/Medicure.git'
      }
   } 
  stage('package the application'){
     steps{
       sh'mvn clean package'
          }
       } 
}
} 
