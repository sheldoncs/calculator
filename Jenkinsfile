pipeline {
  agent any
	
  triggers {
    pollSCM('* * * * *')
  }
	
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
    stage("Build Phase") {
      steps {
        sh "./gradlew test"
      }
    }
	stage("Docker build") {
      steps {
        sh "docker build -t sheldoncs/calculator -f /Dockerfile ."
      }
	}
	
  }
}
