pipeline{
    agent{
        label "node"
    }
    stages{
        stage("Restore dependencies"){
            when{
                anyOf{ 
                    branch "main"
                    branch "feature" } // only exec this stage for main and feature branches
            }
            steps{
                bat "dotnet restore" // resolve dependencies for win machines
            }
            
        }
         stage("Build"){
            when{
                anyOf{ 
                    branch "main"
                    branch "feature" } // only exec this stage for main and feature branches
            }
            steps{
                bat "dotnet build --no-restore" // build the project for win machines
            }
            
        }
            stage("Test"){
                when{
                    anyOf{ 
                        branch "main"
                        branch "feature" } // only exec this stage for main and feature branches
                }
                steps{
                    bat "dotnet test --no-build --verbosity normal" // run tests for win machines
                }
                
            }
    }
}