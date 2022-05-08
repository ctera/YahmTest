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
                node {
                    def comment = pullRequest.comment('This PR is highly illogical..')
                }
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
