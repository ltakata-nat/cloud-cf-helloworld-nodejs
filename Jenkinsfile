@Library('piper-lib-os') _
node('k8s-base') {
    agent {
        label "k8s-base"
    }
    stage('prepare') {
        checkout scm
        setupCommonPipelineEnvironment script:this
    }
    stage('Install Dependencies') {
        sh 'npm install'        
    }
    stage('build') {
        mtaBuild script: this
    }
    stage('Install Plugins') {
        sh 'cf install-plugin multiapps -f'
    }
    stage('deploy') {
    cloudFoundryDeploy script: this
}
}