node {
  
  checkout scm
  def imgVersion = UUID.randomUUID().toString()
  def dockerImage = "mukulxinaam/rewardpartner-stage-backend:${imgVersion}"
  def Namespace = "default"
  def PushToregistry = false

  if (params.PushToregistry == 'No'){
    stage('Build image') {
     sh "docker build -t ${dockerImage} ."
    }
  }
 if (params.PushToregistry == 'Yes'){
    stage('Build image') {
      sh "docker build -t ${dockerImage} ."
    }
    stage('Push image') {

        withCredentials([string(credentialsId: 'dockerhub-mukul', variable: 'dockerhubPwd')]) {
            sh "docker login -u mukulxinaam -p ${dockerhubPwd}"
        }
            sh "docker push ${dockerImage}"
    }
  }
}
