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
  stage('test report'){
    steps{
    publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '/var/lib/jenkins/workspace/Medicure/target/surefire-reports', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
           }
  }
  }
} 
