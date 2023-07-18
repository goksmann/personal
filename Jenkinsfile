pipeline{
    agent any
    tools{
        jdk 'JDK'
        maven 'Maven'
    }
    stages{
        stage('Git Checkout'){
            git branch: 'ci-jenkins', url: 'https://github.com/goksmann/personal.git'
        }
    }
}