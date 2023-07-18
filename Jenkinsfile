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
        stage('Test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('Build'){
            steps{
                sh 'mvnclean  install'
            }
        }
        stage('Integration Testing'){
            steps{
                sh 'mvn verify -DiskipUnitTests'
            }
        }
    }
}