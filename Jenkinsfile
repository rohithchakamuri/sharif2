pipeline{
    environment { 
        registry = "sharifdocker123/docker-jenkins-integration-sample" 
        registryCredential = 'sharifdocker123-ansarbasha786'
        dockerImage = ''
    }
    agent any {
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
}
