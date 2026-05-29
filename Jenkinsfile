pipeline {
    agent any
    stages {
        stage ('scm') {
            steps {
                git branch:'main', url: 'https://github.com/devops-bhanu1/idioms.git'
            }
        }
        stage ("Archive the Artifacts") {
            steps {
                archiveArtifacts '**/*.*'
            }
        }
        stage ('Build') {
            steps {
                sshPublisher(publishers: [sshPublisherDesc(configName: 'webserver1', transfers: [sshTransfer(excludes: '', execCommand: '', execTimeout: 120000, flatten:true, makeEmptyDirs: false, noDefaultExcludes:false, patternSeparator: '[, ]+', remoteDirectory:'www/html', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*.*')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: true)])
            }
        }
    }
}
