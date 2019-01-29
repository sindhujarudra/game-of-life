pipeline 
{
    agent any
     stages
    {
      stage('BUILD')
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


