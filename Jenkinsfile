pipeline{
    agent any
    tools{
        jdk 'JDK'
        maven 'Maven'
    }
    stages{
        stage('Git Checkout'){
            steps{
                git branch: 'ci-jenkins', url: 'https://github.com/goksmann/personal.git'
            }
        }
        stage ('BUILD THE APPLICATION FROM GITHUB') {
            steps{
                sh 'mvn install -DeskipunitTests'
            }
        }
        stage ('TEST THE APPLICATION') {
            steps{
                sh 'mvn test'
            }
        }
        stage ('UNIT TEST') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Sonar Scanner'){
            steps{
                withSonarQubeEnv(credentialsId: 'batch-3',installationName: 'SonarQube') {
                    sh 'mvn sonar:sonar'
                }
           }
        }
        stage('Quality Gate'){
            steps{
                waitForQualityGate abortPipeline: false, credentialsId: 'batch-3'
            }
        }
        stage('Uploading War'){
            step{
                 nexusArtifactUploader artifacts: [[artifactId: 'vprofile', classifier: '', file: 'target/vprofile-v2.war', type: 'war']], credentialsId: 'nexus-jenkins', groupId: 'com.visualpathit', nexusUrl: '3.17.174.116:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'vpro-maven', version: 'v2'
            }
        }
    }