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
