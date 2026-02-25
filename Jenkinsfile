pipeline{
    agent {
        label 'agent-1'
    }
    /* environment{
        course="jenkins"
    } */
    options {
                // timeout(time: 10, unit: 'SECONDS') 
                disableConcurrentBuilds()
                retry(3)
    }
    /* parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

    } */

    stages{
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