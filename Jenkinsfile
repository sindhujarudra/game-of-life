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
                echo 'testing..'
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
                failure {
                    mail to: 'sindhu.rudra15@gmail.com', 
                    subject:'$(currentBuild.fullDisplyName) Build Failure'
                      }
               }
         }
    }  
}


