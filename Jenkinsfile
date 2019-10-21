podTemplate( label: env.DIND_CI_CD_DEFAULT_POD_LABEL, cloud: env.DIND_CI_CD_DEFAULT_CLOUD_NAME, inheritFrom: env.DIND_CI_CD_PHP_POD_TEMPLATE_NAME ) {
  node(env.DIND_CI_CD_DEFAULT_POD_LABEL) {
    container(env.DIND_CI_CD_DEFAULT_CONTAINER_NAME) {
      try {
          checkout(scm).each { k,v -> env.setProperty(k, v) }

          // ====== 项目 ci/cd stage 从此处开始编写 ======
          stage('Build') {
              sh '''
                echo "在这里编写：构建任务"
              '''
          }

          stage('Deploy-dev') {
              def stageBranchs = ['dev'];
              if (false == stageBranchs.contains(env.GIT_BRANCH)) {
                currentBuild.result = 'SUCCESS'
                return
              }

              sh '''
                echo "在这里编写：部署任务-开发环境"
              '''
          }

          stage('Deploy-stage') {
              def stageBranchs = ['stage'];
              if (false == stageBranchs.contains(env.GIT_BRANCH)) {
                currentBuild.result = 'SUCCESS'
                return
              }

              sh '''
                echo "在这里编写：部署任务-预发环境"
              '''
          }

          stage('Deploy-prod') {
              def stageBranchs = ['master'];
              if (false == stageBranchs.contains(env.GIT_BRANCH)) {
                currentBuild.result = 'SUCCESS'
                return
              }

              sh '''
                echo "在这里编写：部署任务-生成环境"
              '''
          }
          // ====== 项目 ci/cd stage 编写到此处结束 ======

      } catch (err) {
        currentBuild.result = 'FAILURE'
        env.setProperty('BUILD_ERROR_MESSAGE', err.getMessage())
        
        sh '''
          echo "流水线执行失败，错误信息：${BUILD_ERROR_MESSAGE}"
        '''
      }
    }
  }
}