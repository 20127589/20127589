node {
    checkout scm
    
    docker.withRegistry('hhtps://registry.hub.docker.com','dockerhub'){
        def customImage = docker.build("2imfatx/20127589")
        customImage.push()
    }
}
