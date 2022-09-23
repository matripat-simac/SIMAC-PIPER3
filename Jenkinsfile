@Library('piper-lib-os') _

node() {

    stage('prepare') {
        checkout scm
        setupCommonPipelineEnvironment script:this
    }

    stage('build') {
        mtaBuild script: this
    }

    stage('deploy') {
        cloudFoundryDeploy(
            script: this,
            cloudFoundry: [org: 'Simac IT NL B.V._devops-toolchain-5nhqwfg7', apiEndpoint: 'https://api.cf.eu10-004.hana.ondemand.com', space: 'DevOps', credentialsId: 'CF_CREDENTIALSID']
        )
    }
}
