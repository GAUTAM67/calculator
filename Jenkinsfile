pipeline {
agent any
stages {
    stage("Compile") {
      steps {
        sh "./gradlew compileJava"
      }
    }
	  
    stage("Unit test") {
      steps {
        sh "./gradlew test"
      }
    }
   stage("Code Coverage") {
     steps {
       sh "./gradlew jacocoTestReport"
	publishHTML (target : [
	 reportDir: 'build/reports/jacoco/test/html',
	 reportFiles: 'index.html',
	 reportName: "JaCoCo report"
	])
       sh "./gradlew jacocoTestCoverageVerification"
}
}
stage ("Static code analysis")  {
steps {
sh "./gradlew checkstyleMain"
}
}
}
}
