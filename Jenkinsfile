pipeline{
agent any
stages {
stage("Get dir size") {
    steps {
    script {
      DIR_SIZE = sh(returnStdout: true, script: "git describe --tags `git rev-list --tags --max-count=1` ")
    }
    echo "dir size = ${DIR_SIZE}"
    echo  "${env.GIT_BRANCH}"
        script{
    if ("${DIR_SIZE}".contains("pipeline")) {
              //when { tag pattern: '^sonar-*', comparator: "REGEXP" }
                     script{
                    zip archive: true, dir: 'pipeline_compressor', glob: '', zipFile: 'pipeline_compressor.zip'
                }
            }    
                else{
                     script{
                    zip archive: true, dir: 'S3Fetch', glob: '', zipFile: 'S3Fetch.zip'
                }
            }
  }
    }
}
}
}
