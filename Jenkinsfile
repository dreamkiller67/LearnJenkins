pipeline {
  agent any
  stages {
    stage("Build") {
      steps {
          // Run the maven build
          sh "mvn clean verify"
       // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe & FindBugs & SpotBugs reports...
      }
    }
  }
}
