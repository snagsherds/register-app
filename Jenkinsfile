

pipeline {

  //define the jenkins agent//
  agent { label 'Jenkins-Agent' }
  
  //recall the tools used //
  tools {
    jdk 'java17'
    maven 'Maven3'  
  }

  //jenkins stages
  stages {


    
    //the stage will clean the workspace directory//
    stage("cleanup workspace"){
      steps {
        cleanWs()            
      }
    }
    
    //checkout the code from github to jenkins agent//
    stage("checkout from SCM") {
      steps {
        git branch: 'main', credentialsId: 'github', url: 'https://github.com/snagsherds/register-app'        
      }
    }

    //this stage will build the application using maven by first clean the old build hence mvn clean package//
    stage("Build Application"){
      steps {
        sh "mvn clean package"
      }
    }

    //this stage will test the application with maven//
    stage("Test Application"){
      steps{
        sh "mvn test"
      }
    }

  
  }
  
}
