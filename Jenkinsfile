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
            cloudFoundry: [org: '30c12a2ctrial', apiEndpoint: 'https://api.cf.ap21.hana.ondemand.com', space: 'dev', credentialsId: 'CF_CREDENTIALSID']
        )
    }
}
