pipeline 
   {
      agent any
      stages
	   {
          stage ('Build')
		    {
              steps 
			{
                sh 'mvn clean package'
            }
            post 
			{
                success 
				{
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }      
        } 
            stage ('Deploy to staging')
			{
			  parallel
			   {
			     stage ('Deploy to staging')
				   {
                     steps
			          {
                          build job: 'deploy-to-staging'
                        } 
                    }
				 stage ('Deploy-Prod')
				  {
				     steps
				      {
					     build job: 'deploy-prod'
			            }	  
			        }			
			    }  
            }
        }
	}
