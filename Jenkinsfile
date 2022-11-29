pipeline{
agent any
stages {
stage("Get dir size") {
    steps {
    script {
      DIR_SIZE = sh(returnStdout: true, script: "git describe --tags")
    }
    echo "dir size = ${DIR_SIZE}"
        script{
    if (${DIR_SIZE}.contains('pipeline')) {
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
