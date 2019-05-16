

ant -buildfile test.xml
ant -f test.xml -y


node('linux'){
    stage('Test'){
        git ''
         sh 'ant -buildfile test.xml'  
    }

    stage('Build'){
        sh 'ant'
    }
    
    stage('Results'){
        junit 'reports/*.xml'
    }
    
}
