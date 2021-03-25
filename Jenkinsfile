node {
   def mvnHome
   stage('getscm') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/ybmadhu/spring3-mv...​
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'M3'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
      echo 'this is build maven artifact'
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
    stage('artifact') {
      
      archive 'target/*.war'
   }
   stage ('deploy'){
   echo 'deployment started'
       bat '''copy http://18.222.148.118:8085:\\Users\\Madhu\\.jenkins\\workspace\\kelly_pipeline_java_maven\\target\\*.war http://18.222.148.118:8085\\opt\\tomcat\\webapps\\'''
   }
}
