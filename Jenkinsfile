node {
  //def myGradleContainer = docker.image('gradle:jdk8')
  def myGradleContainer = docker.image('gradle:jdk11')
  myGradleContainer.pull()
  stage('prep') {
    checkout scm
  }
  stage('test') {
     myGradleContainer.inside("-v /usr/src/jenkins-data/.gradle:/home/gradle/.gradle") {
       sh 'cd complete && gradle test --stacktrace'
     }
  }
  stage('run') {
     myGradleContainer.inside("-v /usr/src/jenkins-data/.gradle:/home/gradle/.gradle") {
       sh 'cd complete && gradle run'
     }
  }
}
