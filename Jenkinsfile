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
                git 'https://github.com/chetangautamm/docker-demo.git' 
                
            }
        } 
        stage('Building Image') { 
            steps { 
                script { 
                    dockerImage = docker.build registry
                }
            } 
        }
        stage('Deploy our image') { 
            steps { 
                script { 
                    docker.withRegistry( '', registryCredential) { 
                        dockerImage.push() 
                    }
                } 
            }
        }
    }
}

