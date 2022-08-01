pipeline{
    agent{
        label "any"
    }
    stages{
        stage("sonar quality chec"){
            agent {
                docker{
                    image 'openjdk:11'
                }
            }
            steps{
               script{
                 withSonarQubeEnv(credentialsId: 'sonar-token') {
                    sh 'chmod +x gradlew'
                    sh './gradlew sonarqube'
                 }
               }

            }
            
        }
        

        
    }
}