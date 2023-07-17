pipeline{
    agent any
    tools {
        jdk 'JDK'
        maven 'Maven' 
    }
    stages {
        stages ('PULL THE APPLICATION FROM GITHUB') {
            steps{
                git branch: 'ci-jenkins', credentialsId: 'gitlogin', url: 'https://github.com/goksmann/personal.git'
            }
        }
        stage ('FETCH THE CODE FROMGITHUB'){
            steps{
                sh 'mvn install -Deskiptests'
            }
        }
            }
        }
    }

     }
}