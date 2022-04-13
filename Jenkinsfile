pipeline{
    agent any
    stages{
        stage("sonar quality check"){
            agent{
                docker{
                    image 'openjdk:11'
                }
            }
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonarpwd') {
                        sh 'chmod +x gradlew'
                        sh './gradlew sonarqube --stacktrace'
                    }
                }
            }
            
        }
    }
    
}