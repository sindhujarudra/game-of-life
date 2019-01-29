pipeline 
{
    agent any
     stages
    {
         stage('compile')
          {
            steps {
                sh 'mvn compile'
            }
         }
         stage('test')
            {
            steps {
                sh 'mvn test'
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
      } 
}


