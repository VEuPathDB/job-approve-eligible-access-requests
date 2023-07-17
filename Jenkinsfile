#!groovy


node("watermelon") {
  checkout scm
  sh 'curl --location --request POST "https://clinepidb.org/eda/approve-eligible-access-requests?admin-auth-token=`cat ~/service-admin-token`"' --header "Auth-Key: `cat ~/eda-service-user-token`"
}
