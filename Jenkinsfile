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
                        sh 'sudo mkdir /home/.sonar'
                        sh 'sudo chmod 777 /home/.sonar'
                        sh 'sudo ENV SONAR_USER_HOME=/home/.sonar'
                        sh 'chmod +x gradlew'
                        sh './gradlew sonarqube --stacktrace'
                    }
                }
            }
            
        }
    }
    
}