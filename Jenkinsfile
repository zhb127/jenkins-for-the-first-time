// podTemplate 已由系统配置好了，以下为固定变量值，不要修改
def k8sCluoudName = 'ai_k8s_cloud'
def podLabel = 'dind-ci-cd'
def containerName = 'dind-ci-cd'

podTemplate( label: podLabel, cloud: k8sCluoudName) {
  node(podLabel) {
    
    // 从代码仓库，拉取当前分支的最新代码
    // 固定步骤，不要修改
    def scmVars = checkout scm

    withEnv([
      "PROJECT_NAME=jenkins-for-the-first-time",
      "GIT_BRANCH=${scmVars.GIT_BRANCH}",
      "GIT_COMMIT=${scmVars.GIT_COMMIT}",
    ]) {

        // 在默认的容器中，执行流水线的各个阶段，完成 CI/CD
        container(containerName) {
          stage('Build') {
              sh '''
                echo "在这里编写构建逻辑"
                echo "在 sh 包裹的地方，可以写 shell 脚本"
                echo """
在这里可以读取环境变量：${PROJECT_NAME}
来协助完成各种构建需求
                """
              '''
          }
          stage('Test') {
              sh '''
                echo "在这里编写测试逻辑" 
              '''
          }
          stage('Deploy-dev') {
              // 如果条件不满足，则跳过当前 stage，执行下一个 stage
              if( env.GIT_BRANCH != 'dev' ) {
                currentBuild.result = 'SUCCESS'
                return
              }

              sh '''
                echo "在这里编写部署到 dev 环境的逻辑"
              '''
          }
          stage('Deploy-prod') {
              // 如果条件不满足，则跳过当前 stage，执行下一个 stage
              if( env.GIT_BRANCH != 'master' ) {
                currentBuild.result = 'SUCCESS'
                return
              }

              sh '''
                echo "在这里编写部署到 prod 环境的逻辑"
              '''
          }
        }

    }
  }
}