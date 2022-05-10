@Library('devops-library') l1
@Library('vSphere-functions') l2

def dockerhost = getDockerhost()
echo "dockerhost: ${dockerhost}"


pipeline {
    agent {
        node { 
            label "microservices-agent-${dockerhost}"
        }
    }
    
    stages {
        stage("build") {
            steps {
                echo 'Build phase....'
                echo "yahmyahm  ${params.BRANCH_NAME}"
                sh "github-comment post -token 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 -org ctera -repo YahmTest -pr 3 -template test11114201"
                sh "ls -l"
                sh "pwd"

                
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
