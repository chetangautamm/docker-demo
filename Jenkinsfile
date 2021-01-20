pipeline { 
    environment { 
        registry = "chetangautamm/repo" 
        registryCredential = '58881f31-29bb-48a8-9da9-fc254654146d' 
        dockerImage = '' 
    }
    agent any 
    stages { 
        stage('Git Clone') { 
            steps { 
                git 'https://github.com/YourGithubAccount/YourGithubRepository.git' 
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
        stage('Cleaning up') { 

            steps { 

                sh "docker rmi $registry:$BUILD_NUMBER" 
            }
        } 
    }
}

