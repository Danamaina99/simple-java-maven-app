pipeline {
    agent any

    environment {
        MAVEN_HOME = '/opt/apache-maven-3.9.10'
      //  SONARQUBE_SERVER = 'SonarQube'         // Jenkins Sonar config name
    //    IQ_SERVER_URL = 'https://your-iq-server.com'
      //  IQ_APP_ID = 'your-app-id'
    //    CYCLONEDX_VERSION = '2.7.8'
      //  NEXUS_REPO_URL = 'https://your-nexus-repo.com/repository/sbom-repo'
    }

   

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Danamaina99/simple-java-maven-app.git'
            }
        }

        stage('Maven Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('Generate SBOM') {
            steps {
                sh 'mvn org.cyclonedx:cyclonedx-maven-plugin:makeBom'
            }
        }

        stage('Archive SBOM') {
            steps {
                archiveArtifacts artifacts: 'target/bom.xml', fingerprint: true
            }
        }
    }
}
