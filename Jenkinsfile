pipeline {
    agent any
    triggers {
        githubPush()
    }
    
stages {
        stage('Create and Push Mirror repo') {
            steps {
                withCredentials([gitUsernamePassword(credentialsId: 'Gitsync', gitToolName: 'Default')]) {
                sh '''
                rm -rf sync-practise.git || true
                git clone --bare https://github.com/rugmak/sync-practise.git
                ls
                cd  /var/jenkins_home/workspace/first_sync/sync-practise.git/
                git remote set-url --push origin https://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@github.com/pratyaksh-kumar/gitsync_pk.git
                git remote -v
                git fetch -p origin
                ls
                git push --mirror --force https://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@github.com/pratyaksh-kumar/gitsync_pk.git
                '''
                }
                }
            }
        stage('Clear Workspace') {
            steps {
                sh 'pwd'
                sh 'ls -l'
                deleteDir()
            }
                
        }    
    }
}
