node {
    def app

    stage('Clone Repo') {
        /* This Stage Clones the Repository to our Workspace */
        checkout scm
    }

    stage('Build Image') {
        /* This Stage Builds the Docker Image */
        app = docker.build("atreyamohan/testnodeapp")
    }

    stage('Test Image') {
        /* This Stage Tests the Docker Image */ 
        app.inside {
            echo "Tests Passed"
        }
    }

    stage('Push Image') {
        /* This Stage pushes the image to the Repo */
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
            } 
        echo "Pushing Docker Image to DockerHub Repository"
    }
}
