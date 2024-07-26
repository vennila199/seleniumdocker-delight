pipeline{

    agent any

    stages{

        stage('Build Jar'){
            steps{
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Build Image'){
            steps{
                bat 'docker build -t=vennilasanthanam/selenium:latest .'
            }
        }

        stage('Push Image'){
               environment{
                DOCKER_HUB = credentials('dockerhub-creds                                                                                                                                           ')
            }
            steps{
                bat 'docker login -u %DOCKER_HUB_USR% -p %DOCKER_HUB_PSW%'
                bat 'docker push vennilasanthanam/selenium:latest'
                bat "docker tag vennilasanthanam/selenium:latest vennilasanthanam/selenium:${env.BUILD_NUMBER}"
                bat "docker push vennilasanthanam/selenium:latest:${env.BUILD_NUMBER}"
                
        }

    }

   
}

}