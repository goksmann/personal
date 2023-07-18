pipeline{
    agent any
    tools{
        jdk 'JDK'
        maven 'Maven'
    }
    stages{
        stage('GIT CHECKOUT'){
            steps{
                git branch: 'ci-jenkins', url: 'https://github.com/goksmann/personal.git'
            }
        }
        stage('MAVIN BUILD'){
            steps{
                sh 'mvn test'
            }
        }
    }
}