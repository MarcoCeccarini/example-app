node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("getintodevops/example-app")
    }

    stage('Push image') {
        /* Finally, we'll push the image into Docker Hub */

withCredentials([usernamePassword( credentialsId: 'docker-hub-credentials', usernameVariable: 'marcoceccarini', passwordVariable: 'dckr_pat_9XUUqySFFHvp-b8rfID0EruUboE')]) {
        def registry_url = "registry.hub.docker.com/"
        bat "docker login -u $USER -p $PASSWORD ${registry_url}"
        docker.withRegistry("http://${registry_url}", "docker-hub-credentials") {
            // Push your image now
                        app.push("latest")
        }
    
        }
    }
}
