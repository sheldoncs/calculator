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
    stage("Package") {
          steps {
           sh "./gradlew build"
           }
	}
	stage("Docker build and run") {
      steps {
        sh "docker build -t calculator ."
		sh "docker run -p 8085:8080 --name calculator calculator"
      }
	}
	
  }
}
