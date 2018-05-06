node {
  try {
    stage('checkout') {
      checkout scm
    }
    stage('prepare') {
      sh "git clean -fdx"
    }
    stage('Build') {
		steps{
			sh 'mvn -Dmaven.test.failure.ignore=true install'
		}
		post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
    }
    stage('publish') {
      echo "uploading package..."
    }
  } finally {
    stage('cleanup') {
      echo "doing some cleanup..."
    }
  }
}
	