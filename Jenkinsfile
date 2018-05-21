node
{
try
  {

      stage('build')
      {
          sh '''
             ant /build.xml
             '''
      }
      echo 'This will run only if successful'
  }

  catch (e)
  {
      echo 'This will run only if failed'

      // Since we're catching the exception in order to report on it,
      // we need to re-throw it, to ensure that the build is marked as failed
      throw e
  }

  finally
  {
      def currentResult = currentBuild.result ?: 'SUCCESS'
      if (currentResult == 'UNSTABLE')
      {
          echo 'This will run only if the run was marked as unstable'
      }

      if (currentResult == 'SUCCESS')
      {
      echo 'This will run if successful'
      }

