#!groovy

node("watermelon") {
  checkout scm
  sh '''
    responseCode=$(curl -s -o /dev/null -w "%{http_code}" --location --request POST "https://qa.clinepidb.org/eda/approve-eligible-access-requests" --header "admin-token: `cat ~/service-admin-token`")
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
