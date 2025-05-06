pipeline {
    agent any
    environment {
        SONARQUBE_SERVER = 'SonarQubeServer' // The name of the SonarQube server configured in Jenkins
        SONAR_TOKEN = 'sqa_76e834b54e77f11e27382eb035227fcf581b88cc'
        SONAR_SCANNER_OPTS = "-Xmx1024m"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Joonaron/InClassWeek5'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQubeServer') {
                    sh """
                     export PATH="/Users/joonasronimus/Desktop/Period4/sonar-scanner-7.1.0.4889-macosx-aarch64/bin:$PATH"
                    sonar-scanner \
                    -Dsonar.projectKey=InClassWeek5 \
                    -Dsonar.sources=src \
                    -Dsonar.projectName=InClassWeek5 \
                    -Dsonar.host.url=http://localhost:9000 \
                    -Dsonar.login=${env.SONAR_TOKEN} \
                    -Dsonar.java.binaries=target/classes
                    """
                }
            }
        }
    }
}


                 
