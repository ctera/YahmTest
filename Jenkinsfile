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

                withCredentials([string(credentialsId: "Github-API-Token", variable: "TOKEN")]) {
                    sh "github-comment post -token ${TOKEN} -org ctera -repo YahmTest -pr ${env.GIT_BRANCH} -template test1111420"
                }

                
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
