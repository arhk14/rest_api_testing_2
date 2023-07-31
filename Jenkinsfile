pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your GitHub repository
                git url: 'https://github.com/arhk14/rest_api_testing_2.git', credentialsId: 'Git_Authentication'
            }
        }
        
        stage('Run JMeter') {
            steps {
                // Execute your JMeter script using the workspace path
                sh 'wget https://github.com/arhk14/rest_api_testing_2/raw/master/list_of_users_28062023.jmx' 
                sh 'jmeter -n -t list_of_users_28062023.jmx  -l results.jtl'
            }
        }
    }

    post {
        always {
            // Archive the JTL result file for later reference
            archiveArtifacts artifacts: 'results.jtl', onlyIfSuccessful: false
        }
    }
}
