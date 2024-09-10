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
                withCredentials([string(credentialsId: 'DEST', variable: 'DEST')]){
                    sh 'scp -o StrictHostKeyChecking=no -r sources/ "${DEST}"'
                }
               
            }
        }
    }
}
