pipeline {
    
    agent none
    
    stages {
        stage('Matrix Stage') {
                agent {
                    matrix {
                        axes {
                            axis {
                                name 'TARGET'
                                values 'docs','linters','covers'
                            }
                        } 
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
        }        
    }
}
