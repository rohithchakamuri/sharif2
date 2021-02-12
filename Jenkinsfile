pipeline{
    environment { 
        registry = "akanshagiriya/docker-jenkins-integration-sample" 
        registryCredential = '9b3c0f89-68c3-46b7-8b74-f35aea084949'
        dockerImage = ''
    }
    agent any
        stages{
            stage('build'){
                steps{
                    sh 'mvn install'
                }
            }
        }
}
