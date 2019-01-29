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
                  }                  
             }
         }
         stage('Deploy') {
            steps {
                echo 'Deploying'
                sh 'mvn deploy'
            }
        }
         failure {
      // notify users when the Pipeline fails
      mail to: 'sindhu.rudra15@gmail.com',
          subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
          body: "Something is wrong with ${env.BUILD_URL}"
    }
    
}


