node('master'){
    docker.withRegistry('https://registry.hub.docker.com', 'osheen-docker') {
    
        git url: "https://github.com/nagarro-osheen/DockerExample.git", credentialsId: '41248c1e-b278-466e-9a3e-4881c05245f9'
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "Build docker image"
        sh "sudo docker.build -t \"dockerexample\""
	
	stage "Run docker image"
    	sh "sudo docker run dockerexample"

        stage "publish"
        app.push 'master'
    }
}
