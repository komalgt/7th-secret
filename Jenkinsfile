pipeline {
  agent any
  stages {
    stage('Get Secret') {
      steps {
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: 'your-jenkins-aws-creds']]) {
          sh '''
            secret=$(aws secretsmanager get-secret-value --secret-id my_example_secret --query SecretString --output text)
            username=$(echo $secret | jq -r .username)
            password=$(echo $secret | jq -r .password)
            echo "Username is: $username"
            # Use the secrets in your build tasks
          '''
        }
      }
    }
  }
}
