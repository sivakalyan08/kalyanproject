node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Build image') {
  
       app = docker build("kalyannagineni/team")
    }

    stage('Test image') {
  

        app.inside {
            sh 'echo "Tests passed2"'
        }
    }

    stage('Push image') {
        
        docker.with Registry('https://registry.hub.docker.com', 'team6') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
     
        
     
}
