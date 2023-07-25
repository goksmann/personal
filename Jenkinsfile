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
        stage ('BUILD THE APPLICATION FROM GITHUB'){
            steps {
                sh 'mvn install-DeskipTests'
            }
        }
        stage ('TEST THE APPLICATION'){
            steps {
                sh 'mvn test'
            }
        }
    }
}