pipeline {
    
    options {
      timeout(time: 4, unit: 'HOURS') 
    }

    agent any
    
    // environment {
    //     LQS_CREDS = credentials('LQS_credentials_for_ssh')
    // }
            
    stages {
            stage('Delete workspace before build') {
                //agent any
                steps {
                    //deleteDir()
                    cleanWs()
                }
            }
        
            stage('Code Checkout') {
                    steps {
                        //cleanWs()
                        script{
                                git branch: 'master', url: "https://github.com/sachinjangid2k/prod-pipeline-jenkins.git"
                                sh "ls -lart ./*" 
                                // List all branches in your repo. 
                                sh "git branch -a"
                                sh "git checkout master"
                        }
                        sh 'git clean -Xdf'
                    }
            } 
            
            stage('build war file using maven') {
                    steps {
                        script{
                                sh 'mvn clean install'
                        }
                    }
            } 
    }     
}

    
