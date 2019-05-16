

ant -buildfile test.xml
ant -f test.xml -y


node('linux'){
    stage('Test'){
        git 'https://github.com/adammaikkula/java-project.git'
         sh 'ant -buildfile test.xml'  
    }

    stage('Build'){
        sh 'ant'
    }
    
    stage('Results'){
        junit 'reports/*.xml'
    }
    
}
