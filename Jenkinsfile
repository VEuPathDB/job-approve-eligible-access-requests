#!groovy


node("watermelon") {
  checkout scm
  token = sh(
    returnStdout: true,
    script: 'cat ~/service-admin-token'
  )
  sh 'curl --location --request POST "https://clinepidb.org/eda/approve-eligible-access-requests?admin-auth-token=$token"'
}
