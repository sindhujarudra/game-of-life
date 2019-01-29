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
         stage('Test')
            {
            steps {
                echo 'Testing...'
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
                    mail to:"sindu.rudra15@gmail.com
                  }
                   failure {
                     mail to:"sindu.rudra15@gmail.com", body: "Build failed."
                }
          }
      } 
    }
}


