pipeline{
    agent any
    parameters {
        choice(name: 'VERSION' , choices:['1.1.0','1.2.0','1.3.0'],description:'')
        booleanParam(name: 'executeTests' ,defaultValue: true,description:'')
    }   
    stages{
        stage("build"){
          steps{   echo 'building the application...'
        }
      }
         stage("test"){
          when{
              expression{
                  param.executeTests
              }
          } 
          steps{   echo 'building the application...'
        }
      }
        stage("deploy"){
          steps{   
              echo 'building the application...'
              echo "deploying version ${params.VERSION}"
        }
      }
    } 
}    
    