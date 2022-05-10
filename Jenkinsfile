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
                    pr_number = env.GIT_BRANCH.split('-')[1]
                    sh "github-comment post -token ${TOKEN} -org ctera -repo YahmTest -pr ${pr_number} -template test1111420"
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
