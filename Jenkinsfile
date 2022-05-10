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

                script { pr_number = env.GIT_BRANCH.split('-')[1] }
                commentOnGithubPR(repo: "YahmTest", pr_number: "${pr_number}", body: "TEST COMMENT")

                // withCredentials([string(credentialsId: "Github-API-Token", variable: "TOKEN")]) {
                //     script {
                //         pr_number = env.GIT_BRANCH.split('-')[1]
                //         sh "github-comment post -token ${TOKEN} -org ctera -repo YahmTest -pr ${pr_number} -template test1111420"
                //     }
                // }

                
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
    // post {
    //     always {
    //         deleteDir()
    //     }
    //     success {
    //         addGitLabMRComment comment: "Jenkins Build was Successful! See ${BUILD_URL}"
    //     }
    //     failure {
    //         addGitLabMRComment comment: "Jenkins Build Failed! See ${BUILD_URL}"
    //     }
    //     aborted {
    //         addGitLabMRComment comment: "Jenkins Build was Aborted! See ${BUILD_URL}"
    //     }
    //     unstable {
    //         addGitLabMRComment comment: "Jenkins Build was Unstable! See ${BUILD_URL}"
    //     }
    // }
}
