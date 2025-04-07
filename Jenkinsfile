#!groovy

node("watermelon") {
  checkout scm
  sh 'curl --location --request POST "https://qa.clinepidb.org/eda/approve-eligible-access-requests" --header "admin-token: `cat ~/service-admin-token`"'
}
