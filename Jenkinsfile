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

  state('upload ArtifactintoNexus'){
    sh "${mavenHome}/bin/mvn deploy"
  }
}