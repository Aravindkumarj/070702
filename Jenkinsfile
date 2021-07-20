@Library('piper-lib-os') _

node(){
  stage('Prepare')   {
      deleteDir()
      checkout scm
      setupCommonPipelineEnvironment script:this
  }

  stage('Build')   {
      mtaBuild (
            script:this,
            dockerImage: 'devxci/mbtci-alpline'
        )
  }

  stage('Deploy')   {
        cloudFoundryDeploy(
            script: this, 
            deployTool:'mtaDeployPlugin', 
            dockerImage: 'ppiper/cf-cli:latest'
        )
  }
  }