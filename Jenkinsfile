@Library('piper-lib-os') _
node('k8s-base') {
    agent {
        label "k8s-base"
    }
    stage('prepare') {
        checkout scm
        setupCommonPipelineEnvironment script:this
    }
    stage('build') {
        mtaBuild script: this
    }
    stage('Login') {
        sh 'cf login --sso -a https://api.cf.us10.hana.ondemand.com'
    }
    stage('deploy') {
    cloudFoundryDeploy script: this
}
}