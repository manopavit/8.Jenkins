pipeline{
    agent any
    parameters{
      choice(name: 'VERSION',choices: ['1.1.0','1.1.1','1.1.2'],description:'')
      booleanParam(name: 'executeTests',defaultValue:true,description:'')
    }
    stages
    {
        stage("build")
            {
          steps{
              echo 'building the application...'
              echo "building the ${NEW_VERSION}"
               }
            }   
        stage("test"){
            when{
              expression{
                params.executeTests
          }
                }
                 
          steps{
              echo 'testing the application...'
               }
          }    
          
        stage("deploy")
              {
          steps{
              echo 'deploying the application...'
              echo "deployinh version ${params.VERSION}"
               }
        }
      }

}
