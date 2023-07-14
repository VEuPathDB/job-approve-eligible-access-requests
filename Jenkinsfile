#!groovy


node("watermelon") {
  checkout scm
  token = sh(
    returnStdout: true,
    script: 'sudo pconf eda_prod | jq ".\"eda_prod_compute_1.Config\"" | grep -oE "ADMIN_AUTH_TOKEN=[a-zA-Z0-9]+" | cut -d"=" -f2'
  )
  sh 'curl --location --request POST "https://clinepidb.org/eda/approve-eligible-access-requests?admin-auth-token=$token"'
}
