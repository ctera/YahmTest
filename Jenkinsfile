@Library('devops-library') l1
@Library('vSphere-functions') l2

def dockerhost = getDockerhost()
echo "dockerhost: ${dockerhost}"


pipeline {
    agent {
        node { 
            label "microservices-agent-main"
        }
    }
    
    stages {
        stage("build") {
            steps {
                echo 'Build phase....'
                sh "github-comment post -token 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 -org ctera -repo YahmTest -pr 3 -template test1111420"

                
            }
        }

        stage("test") {
            steps {
                echo 'Test phase....'
            }
        }

        stage("deploy") {
            when {
                branch "fix-*"
            }
            steps {
                echo 'Deploy phase....'
            }
        }

    }   
}
