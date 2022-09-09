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
            cloudFoundry: [org: '30c12a2ctrial_mytrial-mrt', apiEndpoint: 'https://api.cf.us10-001.hana.ondemand.com', space: 'DEV', credentialsId: 'CF_CREDENTIALSID']
        )
    }
}
