pipeline {
    agent any
    triggers {
        githubPush()
    }
    
stages {
        stage('Create and Push Mirror repo') {
            steps {
                withCredentials([gitUsernamePassword(credentialsId: 'Jenkins_token', gitToolName: 'Default')]) {
                sh '''
                rm -rf sync-practise.git || true
                git clone --bare https://github.com/rugmak/sync-practise.git
                ls
                cd  /var/jenkins_home/workspace/Syncing_Job/sync-practise.git/
                git remote set-url --push origin https://github.com/pratyaksh-kumar/gitsync_pk.git
                git remote -v
                git fetch -p origin
                ls
                git push --mirror --force https://github.com/pratyaksh-kumar/gitsync_pk.git
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
