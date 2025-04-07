#!groovy

node("watermelon") {
  checkout scm
  sh 'responseCode=$(curl -s -o /dev/null -w "%{http_code}" --location --request POST "https://qa.clinepidb.org/eda/approve-eligible-access-requests" --header "admin-token: `cat /usr/local/home/joeuser/service-admin-token`"); responseCode=$(echo $responseCode | tr -d '\n'); if [ "$responseCode" == "204" ]; then exit 0; else exit 1; fi'
}
