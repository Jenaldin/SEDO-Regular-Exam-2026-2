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
            echo "======== end of Restore stage ========"
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
            echo "======== end of Build stage ========"
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
            echo "======== end of Test stage ========"
         }
      }
   }
   post {
      always {echo "Jenkinsfile execution completed"}
      success { echo "Pipeline succeeded" }
      failure { echo "Pipeline failed" }
   }
}