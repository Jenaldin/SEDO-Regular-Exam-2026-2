pipeline{
   agent any

   stages{
      stage("Restore the dependencies"){
         when {
            branch 'main'
         }
         steps{
            bat "dotnet restore"
            echo "======== end of Restore stage ========"
         }
      }
      stage("Build the app"){
         when {
            branch 'main'
         }
         steps{
            bat "dotnet build --no-restore"
            echo "======== end of Build stage ========"
         }
      }
      stage("Run tests for app"){
         when {
            branch 'main'
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