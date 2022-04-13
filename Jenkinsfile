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
                        sh 'mkdir /home/.sonar'
                        sh 'chmod 777 /home/.sonar'
                        sh 'ENV SONAR_USER_HOME=/home/.sonar'
                        sh 'chmod +x gradlew'
                        sh './gradlew sonarqube --stacktrace'
                    }
                }
            }
            
        }
    }
    
}