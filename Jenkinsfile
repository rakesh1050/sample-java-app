pipeline {
    agent any

    // tools {
    //     // Install the Maven version configured as "M3" and add it to the path.
    //     maven "M2_HOME"
    // }

    stages {
        stage ("Checkout"){
            steps{
                git branch: 'main', url: 'https://github.com/rakesh1050/sample-java-app.git'
            }
        }
        stage('Build') {
            steps {
                // // Run Maven on a Unix agent.
               sh "mvn -Dmaven.test.failure.ignore=true clean package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }  
        }
        stage("Docker Build"){
            steps{
                sh "docker image build -t rakesh1050/sampleapp ."
            }
        }
        stage("Docker Run"){
            steps{
                sh "docker container run -itd -p 8080:8080 rakesh105/sampleapp"
            }
        }
    }
}
