pipeline {
  agent any
  //{
    // removed - docker stuff from initial sample
    //docker {
	//  image 'maven:3-alpine'
	//  args '-v /root/.m2:/root/.m2'
	//}
  //}
  stages {
    stage ('TestVersion') {
	  steps {
	  // simple test of shell version
	  sh 'bash --version'
	  }
	}
    stage('Build') {
	  steps {
	    sh 'mvn -B -DskipTests clean package'
	  }
	}
	// unit test stage
	stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
  }
}