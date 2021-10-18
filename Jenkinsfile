@Library("jenkins-global-library@master") _


devopsPipeline(disableConcurrentBuilds: changeRequest()) {

    com.roche.pfdevops.build.Builder mavenBuilder


    podTemplate(containers: [
        containerTemplate(name: 'jenkins-build-agent', image: 'docker.repository.kiosk.roche.com/pf-devops/jenkins-build-agent:1.0.6-master', ttyEnabled: true, command: 'cat')
    ]) {
        catchError {
            node(POD_LABEL) {
                stageCheckout() {

                    if (changeRequest()) {
                        log "changeRequest"
                    } else {
                        log "notChangeRequestasd"

                    }

                    // Checkout source code
                }

            }
        }
        executeIfBuildStatusNotSuccess {
            pipelineContext.factory.newEmail().send()
        }
    }
}
