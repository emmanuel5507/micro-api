pipeline{
    agent any
    environment{
        DOCKERHUB_USERNAME = "emman777"
        APP_NAME = "api"
        IMAGE_TAG = "${BUILD_NUMBER}"
        IMAGE_NAME = "${DOCKERHUB_USERNAME}" + "/" + "${APP_NAME}"
        REGISTRY_CREDS = 'dockerhub'
    }
        stages{
            stage('Checkout SCM'){
                steps{
                    script{
                        git branch: 'main', url: 'https://github.com/emmanuel5507/micro-api.git'

                    }

                }
                     
            }
            stage('Build Docker image'){
              steps{
                script{
                    docker_image = docker.build "${IMAGE_NAME}"
                }
              }  
            }
            stage('PUSH DOCKER IMAGE'){
              steps{
                script{
                    docker.withRegistry('',REGISTRY_CREDS){
                        docker_image.push("$BUILD_NUMBER")
                        docker_image.push('latest')
                    }
                }
              }  
            }
            stage('Remove old DOCKER IMAGE'){
              steps{
                script{
                    sh "docker rmi ${IMAGE_NAME}:${IMAGE_TAG}"
                    sh "docker rmi ${IMAGE_NAME}:latest"
                    }
                }
              }  
            }
            
 }


    
