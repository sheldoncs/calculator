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
	stage("Docker build") {
      steps {
        sh "docker build -t calculator ."
		
      }
	}
	stage("Docker push") {
		steps {
		sh "docker login --username=sheldoncs --email=sheldon.spencer@gmail.com"
		sh "docker push sheldoncs/calculator"
		}
    }
	
  }
}
