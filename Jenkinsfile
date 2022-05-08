pipeline {
    agent any
    
    stages {
        
        stage("build") {
            steps {
                echo 'Build phase....'

                
            }
        }

        stage("test") {
            steps {
                echo 'Test phase....'
            }
        }

        stage("deploy") {
            when {
                branch "main"
            }
            steps {
                echo 'Deploy phase....'
            }
        }

    }   
}
