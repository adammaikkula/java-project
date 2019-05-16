

ant -buildfile test.xml
ant -f test.xml -y


node('linux'){
    stage('Test'){
        git 'https://github.com/adammaikkula/java-project.git'
        sh 'ant -f test.xml -y'
        sh 'ant -buildfile test.xml'
    }

    stage('Build'){
        sh 'ant -f build.xml -v'
    }
    
     stage('Deploy'){
         sh 'ant aws s3 cp s3://aamhw10'
    }
    
    stage('Results'){
        junit 'reports/*.xml'
    }
    
}
