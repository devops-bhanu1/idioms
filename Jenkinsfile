pipeline {
    agent any
    stages {
        stage ('scm') {
            steps {
                git branch:'main', url: 'https://github.com/A2Znipuna/webapp.git'
            }
        }
        stage ("Archive the Artifacts") {
            steps {
                archiveArtifacts '**/*.*'
            }
        }
        stage ('Build') {
            steps {
                sshPublisher(publishers: [sshPublisherDesc(configName: 'webserver', transfers: [sshTransfer(excludes: '', execCommand: '', execTimeout: 120000, flatten:true, makeEmptyDirs: false, noDefaultExcludes:false, patternSeparator: '[, ]+', remoteDirectory:'www/html', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*.*')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: true)])
            }
        }
    }
}
