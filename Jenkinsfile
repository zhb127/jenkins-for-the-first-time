// ------ 以下环境变量按照项目需求做修改 ------
// - 钉钉通知相关配置项
env.DINGTALK_ACCESS_TOKEN="9dd46fa75abf1a56cd2110c0000d41044f40abc00bb290f9a1a6e4c239fbcf79"; // 钉钉群机器人 access-token
env.DINGTALK_MOBILES="";      // at 指定人员，值格式为：手机号,手机号,手机号；at 所有人，值为：all
// ------ 以上环境变量按照项目需求做修改 ------

podTemplate( label: env.DIND_CI_CD_DEFAULT_POD_LABEL, cloud: env.DIND_CI_CD_DEFAULT_CLOUD_NAME, inheritFrom: env.DIND_CI_CD_BASE_POD_TEMPLATE_NAME ) {
  node(env.DIND_CI_CD_DEFAULT_POD_LABEL) {
    container(env.DIND_CI_CD_DEFAULT_CONTAINER_NAME) {
      try {
          checkout(scm).each { k,v -> env.setProperty(k, v) }

          // ====== 项目 ci/cd stage 从此处开始编写 ======
          stage('Build') {
              sh '''
                echo "在这里编写：构建任务"

                dind-notify-dingtalk -a "${DINGTALK_ACCESS_TOKEN}" -m "${DINGTALK_MOBILES}" -t "$(dind-notify-text -t verify-jenkins-access)"
              '''
          }

          stage('Test-dev') {
              def stageBranchs = ['dev'];
              if (false == stageBranchs.contains(env.GIT_BRANCH)) {
                currentBuild.result = 'SUCCESS'
                return
              }

              sh '''
                echo "在这里编写：测试任务-开发环境"

                dind-notify-dingtalk -a "${DINGTALK_ACCESS_TOKEN}" -m "${DINGTALK_MOBILES}" -t "$(dind-notify-text -t verify-jenkins-access)"
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

                dind-notify-dingtalk -a "${DINGTALK_ACCESS_TOKEN}" -m "${DINGTALK_MOBILES}" -t "$(dind-notify-text -t verify-jenkins-access)"
              '''
          }

          stage('Test-release') {
              def stageBranchs = ['release'];
              if (false == stageBranchs.contains(env.GIT_BRANCH)) {
                currentBuild.result = 'SUCCESS'
                return
              }

              sh '''
                echo "在这里编写：测试任务-预发环境"

                dind-notify-dingtalk -a "${DINGTALK_ACCESS_TOKEN}" -m "${DINGTALK_MOBILES}" -t "$(dind-notify-text -t verify-jenkins-access)"
              '''
          }

          stage('Deploy-release') {
              def stageBranchs = ['release'];
              if (false == stageBranchs.contains(env.GIT_BRANCH)) {
                currentBuild.result = 'SUCCESS'
                return
              }

              sh '''
                echo "在这里编写：部署任务-预发环境"

                dind-notify-dingtalk -a "${DINGTALK_ACCESS_TOKEN}" -m "${DINGTALK_MOBILES}" -t "$(dind-notify-text -t verify-jenkins-access)"
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

                dind-notify-dingtalk -a "${DINGTALK_ACCESS_TOKEN}" -m "${DINGTALK_MOBILES}" -t "$(dind-notify-text -t verify-jenkins-access)"
              '''
          }
          // ====== 项目 ci/cd stage 编写到此处结束 ======

      } catch (err) {
        currentBuild.result = 'FAILURE'
        env.setProperty('BUILD_ERROR_MESSAGE', err.getMessage())
        
        sh '''
          dind-notify-dingtalk -a "${DINGTALK_ACCESS_TOKEN}" -m "${DINGTALK_MOBILES}" -t "$(dind-notify-text -t pipeline-failure)"
        '''
      }
    }
  }
}