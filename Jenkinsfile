node('master'){
    docker.withRegistry('https://registry.hub.docker.com', 'osheen.gulati@nagarro.com:nagarro@123') {
    
        git url: "https://github.com/nagarro-osheen/DockerExample.git", credentialsId: 'osheen.gulati@nagarro.com:nagarro@123'
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "DockerExample"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
