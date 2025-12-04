pipeline {
    agent any

    tools {
        // Ensure this Maven tool is configured in your Jenkins "Global Tool Configuration"
        maven 'Maven 3.8.6'
        jdk 'jdk8'
    }

    environment {
        // You should define these credentials in Jenkins Credentials Manager
        // and bind them here.
        ARTIFACTORY_CREDS = credentials('7e59b761-7e86-402e-bc24-a194c787a656') 
        ARTIFACTORY_USER = "${ARTIFACTORY_CREDS_USR}"
        ARTIFACTORY_PASSWORD = "${ARTIFACTORY_CREDS_PSW}"
    }

    stages {
        stage('Build') {
            steps {
                // We use the -s flag to point to our project-specific settings.xml
                // which uses the environment variables for authentication.
                sh 'mvn clean install -s settings.xml'
            }
        }
    }
}
