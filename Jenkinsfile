node{

   def tomcatWeb = '\\opt\\tomcat\\webapps'
   def tomcatBin = '\\opt\\tomcat\\bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/cubeiplKumar/JenkinsPipelineDemo.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'maven', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
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
   /*stage('Deploy to Tomcat'){
   sh "cp \\target\\JenkinsPipeline.war \"${tomcatWeb}\\JenkinsPipeline.war\""
   }*/

 stage('Deploy to Tomcat'){
     def warfile='JenkinsPipeline.war'
	def deployedwarPath="${tomcatWeb}"
	sh "cp target/${warfile} ${tomcatWeb}"

   
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         sh "${tomcatBin}\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
