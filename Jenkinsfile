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
    }
}   