pipeline{
    agent any
    stages{

        stage('Checkout'){
            steps{
                checkout scm
            }
        }

        stage("Install Requirements"){
            steps{
                bat '''
                python -m pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }
        
        stage("Run App"){
            steps{
                bat '''
                python app.py
                '''
            }
        }
    }
    post{
        success{
            echo "Build Successful"
        }
        failure{
            echo "Build Failed"
        }
        always{
            archiveArtifacts artifacts: 'artifact.txt, out/**', allowEmptyArchive: false 
        }
    }
}
