

ant -buildfile test.xml
ant -f test.xml -y


node('linux'){
    stage('Test'){
        git 'https://github.com/adammaikkula/java-project.git'
        sh 'ant -f test.xml'
        sh 'ant -buildfile test.xml'
    }

    stage('Build'){
        sh 'ant -f build.xml -v'
    }
    
     stage('aws'){
         withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'b0267f50-5ffc-4fbf-a1e3-f4c44748a48e', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
            // some block
            sh 'aws_cloudformation describe-stack-resources --stack-name jenkins --region us-east-1'  
       }
    
    stage('Results'){
        junit 'reports/*.xml'
    }
    
}
