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
	/*stage("Docker push") {
		steps {
		sh "docker login --username=sheldoncs"
		sh "docker push sheldoncs/calculator"
		}
    }*/
	stage("Deploy to staging") {
	    steps {
		   sh "docker run -d -p 8085:8080 --name=runcalc calculator"
		   }
	}
	stage("Acceptance test") {
		steps {
			sleep 60
			sh "./acceptance_test.sh"
		}
    }
	
  }
}
