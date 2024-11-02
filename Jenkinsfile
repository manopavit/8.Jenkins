pipeline{
    agent any
    parameters{
      choice(name: 'VERSION',choices: ['1.1.0','1.1.1','1.1.2'],description:'')
      booleanParam(name: 'executeTests',defaultValue: true, description:'')
    }
    stages
    {
        stage("init")
            {
          steps{
              script{
                   gv = load "script.grrovy"
              }
              echo 'building the application...'
              }
            }   
        stage("build"){
            steps{
              script{
                   gv.build()
                   } 
                }
                
          steps{
              echo 'testing the application...'
               }

        }
              
        stage("test"){
            when {
                   expression {
                             params.executeTests
                   }
            }
        } 
        stage("deploy")
              {
                input{
                    message "Select the environment to deploy to"
                    ok "Done"
                    parameters{
                           choice(name: 'ENV' , choices: ['dev', 'staging' , 'prod'], description: '')
                    }
                }
                steps
                  {
                      gv.deployApp()
                      echo "Deploying to ${ENV}"
                  }
              }  
    }

}
