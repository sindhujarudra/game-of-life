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
  }  
}


