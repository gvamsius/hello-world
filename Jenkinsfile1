
node {
    
    stage('git checkout') {
    git 'https://github.com/gvamsius/hello-world.git'
    }
    
    stage('maven build') {
    sh label: '', script: 'mvn -f pom.xml clean install package'
    }
    
    stage('Ansible deployment'){
    sshPublisher(publishers: [sshPublisherDesc(configName: 'ansible-master', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//opt//ansible//playbooks', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'webapp/target/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false), sshPublisherDesc(configName: 'ansible-master', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ansible-playbook /opt/ansible/playbooks/copywarfile.xml', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
    }
        
}
