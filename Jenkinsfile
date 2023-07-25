pipeline{
    agent any
    tools{
        jdk 'JDK'
        maven 'Maven'
    }
    stages {
        stage ('GIT CHECK') {
            steps(
                git branch: 'ci-jenkins', url: 'https://github.com/goksmann/personal.git'
            )
        }
    }
}