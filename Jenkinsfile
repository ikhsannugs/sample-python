pipeline {
  agent any
  stages {
      stage('Checkout SCM') {
        steps{
          checkout scm
        }
      }
      stage('Unit Test') {
        steps{
          script{
            sh "python Tests/unit_tests/test_views.py"
          }
        }
      }
      stage('Deploy') {
        steps{
          sshagent(credentials : ['vm']) {
            sh 'ssh -o StrictHostKeyChecking=no ikhsan@34.101.235.214 "rm -rf sample-python; git clone https://github.com/ikhsannugs/sample-python.git"'
            sh 'ssh -o StrictHostKeyChecking=no ikhsan@34.101.235.214 "cd /home/ikhsan/sample-python; rm -rf .git Jenkinsfile Tests README.md"'
          }
        }
      } 
  }
}
