pipeline{
   agent any

   stages{
      stage("Restore the dependencies"){
         when {
            expression {
               return env.GIT_BRANCH == 'origin/main'
            }
         }
         steps{
            bat "dotnet restore"
            echo "======== executing Restore stage ========"
         }
      }
      stage("Build the app"){
         when {
            expression {
               return env.GIT_BRANCH == 'origin/main'
            }
         }
         steps{
            bat "dotnet build --no-restore"
            echo "======== executing Build stage ========"
         }
      }
      stage("Run tests for app"){
         when {
            expression {
               return env.GIT_BRANCH == 'origin/main'
            }
         }
         steps{
            bat "dotnet test --no-build --verbosity normal"
            echo "======== executing Test stage ========"
         }
      }
   }
}