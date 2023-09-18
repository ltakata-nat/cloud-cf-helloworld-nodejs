@Library('piper-lib-os') _
node() {
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
}