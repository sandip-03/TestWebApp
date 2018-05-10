node {
   stage('Preparation') { 
      git 'https://git@github.com/sandip-03/TestWebApp.git'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
	 sh 'mvn -B -DskipTests clean package'
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.war'
   }
}
