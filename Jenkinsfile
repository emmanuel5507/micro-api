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
        }

    
}