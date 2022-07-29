pipeline {
    
    agent any
    
    stages {
        
        stage('First Stage') {
            steps {
                sh "exit 0"
            }
            
        }
        
        stage('Second Stage') {
            steps {
                echo "BRANCH NAME: " + env.GIT_BRANCH
            }
         stage('Update GIT') {
            steps {
                script {
                    catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                            sh "git add ."
                            sh "git commit -m 'Triggered Build: ${env.BUILD_NUMBER}'"
                            sh "git push https://github.com/EwelinaCh/ci-cd-training main"
                        }
                      }
                    }
                  }
        }        
    }
}
