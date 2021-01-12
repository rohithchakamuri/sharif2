pipeline{
    environment { 
        registry = "sharifdocker123/docker-jenkins-integration-sample" 
        registryCredential = 'eb4e11c9-1c5b-46c8-85f9-4fec06036ac2'
        dockerImage = ''
    }
    agent any
        stages{
            stage('build'){
                steps{
                    sh 'mvn install'
                }
            }

            stage('Building our image') { 
                steps { 
                    script { 
                        dockerImage = docker.build registry + ":$BUILD_NUMBER" 
                    }
                }
            }

            stage('Deploy our image') { 
                steps { 
                    script { 
                        docker.withRegistry( '', registryCredential ) { 
                            dockerImage.push() 
                        }
                    }    
                }
            }

        }
}
