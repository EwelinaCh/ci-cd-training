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
            
        }        
    }
}
