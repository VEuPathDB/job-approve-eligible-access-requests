pipeline {
  agent {
    node {
      label "pineapple"
    }
  }

  stages {
    stage('Run') {
      environment {
        ADMIN_TOKEN = credentials('1546447f-7d6d-40fe-addb-873a9bb78f6e')
      }
      steps {
        sh '''
          responseCode=$(curl -s -o /dev/null -w "%{http_code}" --location --request POST "https://w1.clinepidb.org/eda/approve-eligible-access-requests" --header "admin-token: $ADMIN_TOKEN")
          responseCode=$(echo $responseCode | perl -pe 'chomp')
          if [ "$responseCode" == "204" ]; then
            echo "Eligible access request approval successful."
            exit 0
          else
            echo "Eligible access request approval failed; endpoint returned response status $responseCode"
            exit 1
          fi
        '''
      }
    }
  } 
  
  post {
    unsuccessful {
     slackSend(
        channel: "#alert-scheduled-jobs",
        color: 'danger',
        message: """SCHEDULED JOB FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' Check console output at ${env.BUILD_URL}"""
      ) 
    }
  }

}
