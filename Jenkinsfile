#!groovy

def handleCheckout = {
    sh "echo 'Checkingout branch...'"
    checkout scm
}



node() {
    stage('Code Checkout') {
        handleCheckout()
        sh "git branch -vv"
}
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
}

