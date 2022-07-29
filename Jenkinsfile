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
                        withCredentials([usernamePassword(credentialsId: 'example-secure', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                            def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                            sh "git config user.email admin@example.com"
                            sh "git config user.name example"
                            sh "git add ."
                            sh "git commit -m 'Triggered Build: ${env.BUILD_NUMBER}'"
                            sh "git push https://${GIT_USERNAME}:${encodedPassword}@github.com/${GIT_USERNAME}/example.git"
                        }
                      }
                    }
                  }
                }
        }        
    }
}
