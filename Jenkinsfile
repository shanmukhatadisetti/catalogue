pipeline{
    agent {
        label 'agent-1'
    }
    environment{
        appversion=''
        REGION="us-east-1"
        ACCOUNT_NO="430774481266"
        PROJECT="roboshop"
        COMPONENT="catalogue"
    }
    options {
                // timeout(time: 10, unit: 'SECONDS') 
                disableConcurrentBuilds()
                retry(3)
    }
    /* parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

    } */

    stages{
        stage('Read package.json version') {
            steps {
                script {
                def pkg = readJSON file: 'package.json'
                appVersion = pkg.version
                echo "Package version is ${appVersion}"
                }
            }
        }
        stage('Install Dependencies'){
            steps{
                script{
                    sh """
                        npm install
                    
                    """

                }
            }
        }
        stage('Docker Build'){
            steps{
                script{
                    withAWS(credentials: 'aws-creds', region: 'us-east-1') {
                       sh """
                            aws ecr get-login-password --region ${REGION} | docker login --username AWS --password-stdin ${ACCOUNT_NO}.dkr.ecr.us-east-1.amazonaws.com
                            docker build -t ${ACCOUNT_NO}.dkr.ecr.us-east-1.amazonaws.com/${PROJECT}/${COMPONENT}:${appVersion}
                            docker push ${ACCOUNT_NO}.dkr.ecr.us-east-1.amazonaws.com/${PROJECT}/${COMPONENT}:${appVersion}
                       """
                    }

                }
            }
        }
    }
}