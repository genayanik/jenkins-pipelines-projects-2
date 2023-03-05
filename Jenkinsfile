node{
  def  mavenHome  = tool name:  'maven3.9.0'
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
 

}