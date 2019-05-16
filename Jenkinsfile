node('linux'){
    stage('Unit Test'){
        git 'https://github.com/adammaikkula/java-project.git'
        junit 'ant -f test.xml'
        junit 'ant -buildfile test.xml'
    }

    
     stage('aws'){
         withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'b0267f50-5ffc-4fbf-a1e3-f4c44748a48e', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
            // some block
            sh 'aws_cloudformation describe-stack-resources --stack-name jenkins --region us-east-1' 
            sh 'aws s3 cp rectangle-12.jar s3://aamhw10'
     }
         
     stage('Build'){
        sh 'ant -f rectangle-12.jar -v'
    }
         
    stage('Results'){
        junit 'reports/*.xml'
    }
    
}
