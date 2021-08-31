node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Build image') {
  
       app = docker build https://github.com/docker/rootfs.git#container:docker
    }

    stage('Test image') {
  

        app.inside {
            sh 'echo "Tests passed2"'
        }
    }

    stage('Push image') {
        
        docker.withRegistry('https://registry.hub.docker.com', 'team6') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
     
        
     
}
