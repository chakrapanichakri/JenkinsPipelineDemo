node{

   def tomcatWeb = 'C:\\tomcat\\webapps'
   def tomcatBin = 'C:\\tomcat\\bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/chakrapanichakri/JenkinsPipelineDemo'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome = tool 'M3'   
      bat "${mvnHome}/bin/mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     bat "copy target\\JenkinsPipeline.war \"${tomcatWeb}\\JenkinsPipeline.war\""
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         bat "${tomcatBin}\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
