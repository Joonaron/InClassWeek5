pipeline {
 agent any
 environment {
 SONARQUBE_SERVER = 'SonarQubeServer' // The name of the SonarQube server configured in
Jenkins
 SONAR_TOKEN = 'sqa_811a5cc5d65fa5e1c39d48cb699a1b4967a87512'
 }
 stages {
 stage('Checkout') {
 steps {
 git branch: 'master', url: 'https:'github.com/ADirin/sep2_week5_inclass_s2.git'
 }
 }
 stage('Build') {steps {
                  sh 'mvn clean install'
                  }
                  }
                  stage('SonarQube Analysis') {
                  steps {
                  withSonarQubeEnv('SonarQubeServer') {
                  sh """
                  sonar-scanner ^
                  -Dsonar.projectKey=devops-demo ^
                  -Dsonar.sources=src ^
                  -Dsonar.projectName=DevOps-Demo ^
                  -Dsonar.host.url=http://localhost:9000 ^
                  -Dsonar.login=${env.SONAR_TOKEN} ^
                  -Dsonar.java.binaries=target/classes
                  """
                  }
                  }
                  }
                  }
                 }
