node {
    def app

    def usernameVariable= 'marcoceccarini'
    def passwordVariable= 'dckr_pat_9XUUqySFFHvp-b8rfID0EruUboE'
        
    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("marcoceccarini/example-app")
    }

    stage('Push image') {
        /* Finally, we'll push the image into Docker Hub */

  docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("latest")
        }
    }
}
/* trig */