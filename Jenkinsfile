node {
   def mvnHome
   stage('Code-Checkout') { // for display purposes
      //Checkout code from a GitHub repository
      git 'https://github.com/ybmadhu/spring3-mvc-maven-xml-hello-world.git'
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
      bat '''copy C:\\Users\\prasanth.pamula\\.jenkins\\workspace\\hello-world\\target\\*.war C:\\Users\\prasanth.pamula\\Downloads\\apache-tomcat-8.5.38\\webapps\\'''
   }
}




