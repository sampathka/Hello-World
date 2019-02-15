node {
   properties([parameters([choice(choices: ['master', 'dev', 'qa', 'staging'], description: 'Choose branch to build and deploy', name: 'gitBranch')]), pipelineTriggers([pollSCM('')])])
   def mvnHome
   stage('Code-Checkout') { // for display purposes
      //Checkout code from a GitHub repository
      git 'https://github.com/sampathka/Hello-World.git'
      // Getting maven installation location and letting know to jenkins 
      // **       in the global configuration.           
      mvnHome = tool 'Maven'
   }
   stage('Code-Build') {
      //maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
      echo 'this is build maven artifact'
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   
   stage ('artifact-deploy-to-tc-instance'){
   echo 'deployment started'
      //sh label: '', script: 'cp /root/MavenHelloWorldProject/target/*.war /opt/tomcat/apache-tomcat-8.5.38/webapps/'
   }
}




