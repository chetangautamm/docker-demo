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
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '0280c339-f1a8-48bc-b303-3ec7a661b546', url: 'https://github.com/chetangautamm/docker-demo.git']]])
                
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

