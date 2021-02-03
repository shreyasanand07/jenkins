#!/usr/bin/groovy

pipeline {
    agent any
    
    environment {
        // This can be nexus3 or nexus2 server
        NEXUS_VERSION = "nexus3"
        // This can be http or https
        NEXUS_PROTOCOL = "http"
        // Where your Nexus is running
        NEXUS_URL = "10.22.21.138:8081"
        // Repository where we will upload the artifact
        NEXUS_REPOSITORY_RELEASES = "maven-releases"
        NEXUS_REPOSITORY_SNAPSHOTS = "maven-snapshots"
        // Jenkins credential id to authenticate to Nexus OSS
        NEXUS_CREDENTIAL_ID = "899bfb86-db46-3333-939e-464185476a57"
    }
    
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }  
}  
