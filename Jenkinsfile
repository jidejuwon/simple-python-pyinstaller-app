pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                sh 'python3 -m py_compile sources/add2vals.py sources/calc.py' 
                stash(name: 'compiled-results', includes: 'sources/*.py*') 
            }
        }
        stage('Deploy') {
            steps{
                // withCredentials([string(credentialsId: 'DEST', variable: 'DEST')]){
                    sh 'scp -r sources/ root@95.216.167.245:/root/jenkins'
                // }
               
            }
        }
    }
}
