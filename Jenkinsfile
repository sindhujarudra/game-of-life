pipeline 
{
    agent any
     stages
    {
         stage('Compile')
          {
            steps {
                echo 'compiling..'
                sh 'mvn compile'
            }
         }
        
        stage('Run Tests') {
            parallel {
                stage('Test On Windows') {
                    agent {
                        label "windows"
                    }
                    steps {
                        bat "run-tests.bat"
                    }
                    post {
                        always {
                            junit "**/TEST-*.xml"
                        }
                    }
                }
                stage('Test On Linux') {
                    agent{
                        label "linux"
                    }
                    steps {
                        sh "run-tests.sh"
                    }
                    post {
                        always {
                            junit "**/TEST-*.xml"
                        }
                    }
                }
            }
        }
          stage('Package')
           {
            steps {
                sh 'mvn package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                  }                  
             }
         }
         stage('Deploy') {
            steps {
                echo 'Deploying'
                sh 'mvn deploy'
            }
        }
  }  
}


