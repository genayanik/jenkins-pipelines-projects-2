node{
  def  mavenHome  = tool name:  'maven'
  stage('1SCMCLONE'){
    git 'https://github.com/Lion-Technology-Solutions/jenkins-pipelines-projects-2.git'
  }
  stage ('install+test+build'){
    sh   "${mavenHome}/bin/mvn clean package"
  }
  stage('codequality-Analysis'){
    sh "${mavenHome}/bin/mvn sonar:sonar"
  }

  stage('upload ArtifactintoNexus'){
   sh "${mavenHome}/bin/mvn deploy"
  }

  stage('deploy2TestEnv')
    sh "echo 'DevOps is making Lots of sense'"
      deploy adapters: [tomcat9(credentialsId: 'tomcat-user-deploy', path: '', url: 'http://3.98.138.118:8009/')], contextPath: 'project-cicd-2', war: 'target/*.war'
 
  stage('send build status notifications to ms teams'){
    office365ConnectorSend color: 'red', message: 'Lion Tech DevOps Engineers Automating', status: 'Keep up the good work', webhookUrl: 'https://liontechacademy.webhook.office.com/webhookb2/69fa68d2-9fe7-4e6f-975a-7e5715e102a6@b290c85e-0692-4ada-8f25-2a3b60aca73e/JenkinsCI/3c36e8bbbd954f1eaf9760290f8ae2a3/90dc930a-1d3a-4c50-9c2d-39d010312f55'
  }
}