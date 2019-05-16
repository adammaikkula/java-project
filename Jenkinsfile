

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
         sh 'aws_cloudformation describe-stack-resources --stack-name jenkins --region us-east-1'  
    }
    
    stage('Results'){
        junit 'reports/*.xml'
    }
    
}
