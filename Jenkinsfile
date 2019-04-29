properties([pipelineTriggers([githubPush()])]) 

node('linux'){
    stage('Build'){
        git 'https://github.com/kerij/java-project.git'
        sh "ant -f build.xml -v"
    }
    
    stage('Test'){
        sh "ant -f test.xml -v"
    }
    
    stage('Deploy'){
        withAwsCli(
            sh "aws s3 cp ./dist/rectangle-${BUILD_NUMBER}.jar s3://hw10-kerij-jenkins-bucket/rectangle-$BUILD_NUMBER.jar"
            )
    }
    
    stage('Report'){
        
    }
}
