node {
    def app

    stage('Clone repository') {

        checkout scm
    }

    stage('Build image') {
  
       app = docker.build("jideoni/vite-react-resume")
    }

    stage('Test image') {

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        
        docker.withRegistry('https://registry.hub.docker.com', 'Git-hub-Credentials') {
            app.push("${env.BUILD_NUMBER}")
        }
    }
}
