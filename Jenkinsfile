pipeline{
    agent any 
    environment{
        VERSION = "${env.BUILD_ID}"
    }
    stages{
        stage("sonar quality check"){
            agent {
                docker {
                    image 'openjdk:11'
                }
            }
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonar-token') {
                            sh 'chmod +x gradlew'
                            sh './gradlew sonarqube'
                    }
<<<<<<< HEAD

                    timeout(time: 1, unit: 'HOURS') {
                      def qg = waitForQualityGate()
                      if (qg.status != 'OK') {
                           error "Pipeline aborted due to quality gate failure: ${qg.status}"
                      }
                    }

                }  
            }
        }
        stage("docker build & docker push"){
            steps{
                script{
                     withCredentials([string(credentialsId: 'nexusdocker pass', variable: 'docker_pass')]){
                             sh '''
                                docker build -t 54.227.81.167:8083/springapp:${VERSION} .
                                docker login -u admin -p $docker_password 54.227.81.167:8083 
                                docker push  54.227.81.167:8083/springapp:${VERSION}
                                docker rmi 54.227.81.167:8083/springapp:${VERSION}
                            '''
                    }
                }
            }
        }
    }
}   
=======
>>>>>>> 3d2a9fd40c5b829de80e177b1cd5d8de0ceb675f
