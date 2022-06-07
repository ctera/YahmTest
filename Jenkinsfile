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
                                
                sh "ls -l"
                sh "pwd"
                // sh "skipper make clean rpm"
                sh "rpmbuild -bb -vv --define='_srcdir $(PWD)' --define='_topdir $(RPM_BUILD_ROOT)' deploy/ctera-messaging-ansible.spec"
                sh "ls -l"
                
            }
        }
        stage("deploy") {
            when {
                branch "PR*"
            }
            steps {
                echo 'Sending artifacts'
            }
        }
        stage("deploy") {
            when {
                branch "main"
            }
            steps {
                echo 'sending artifacts and coping to \\vgwversions-gen\\versions'
            }
        }

    }
    post {
        always {
            deleteDir()

            script { pr_number = env.GIT_BRANCH.split('-')[1] }
        }
        success {
            commentOnGithubPR("YahmTest", "${pr_number}", "Build was successful! See at ${env.BUILD_URL}")
        }
        failure {
            commentOnGithubPR("YahmTest", "${pr_number}", "Build failed! See at ${env.BUILD_URL}")
        }
        aborted {
            commentOnGithubPR("YahmTest", "${pr_number}", "Build aborted! See at ${env.BUILD_URL}")
        }
        unstable {
            commentOnGithubPR("YahmTest", "${pr_number}", "Build unstable! See at ${env.BUILD_URL}")
        }
    }
}
