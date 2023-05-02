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
   stage('docker image creation'){
    steps{
     sh 'docker build -t kavanapc/medicure:v1 .'  
}
}
     stage('docker login'){
      steps{
      withCredentials([usernamePassword(credentialsId: 'dockerlogin', passwordVariable: 'passwd', usernameVariable: 'kavana')]) {
     sh "docker login -u ${env.kavana} -p ${env.passwd}"
}
   }
     }
   stage('docker push'){
     steps{
      sh 'docker push kavanapc/medicure:v1'
      }
   }
}
} 
