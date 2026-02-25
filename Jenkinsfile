pipeline{
    agent {
        label 'agent-1'
    }
    environment{
        appversion=''
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
        stage('build'){
            steps{
                script{
                    sh """
                    echo 'building....'
                    
                    """

                }
            }
        }
       
    }
}