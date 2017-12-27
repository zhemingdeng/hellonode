node("docker"){
  docker.withRegistry('zhemingdeng/hellonode','zhemingdeng'){
    git url:"https://github.com/zhemingdeng/hellonode.git", credentialsId='zhemingdeng'
    sh "git rev-parse HEAD > .git/commit-id"
    def commit_id=readFile('.git/commit-id').trim()
    println commit_id
    
    stage "build"
    def app=docker.build "hellonode"
   
    stage "publish"
    app.push "master"
    app.commit "${commit_id}"
  }



}
