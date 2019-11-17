// ------ 以下环境变量按照项目需求做修改 ------
env.DIND_CI_CD_POD_TEMPLATE_NAME=env.DIND_CI_CD_BASE_POD_TEMPLATE_NAME
// - 钉钉通知相关配置项
env.DINGTALK_ACCESS_TOKEN="9dd46fa75abf1a56cd2110c0000d41044f40abc00bb290f9a1a6e4c239fbcf79"; // 钉钉群机器人 access-token
env.DINGTALK_MOBILES="";      // at 指定人员，值格式为：手机号,手机号,手机号；at 所有人，值为：all
// ------ 以上环境变量按照项目需求做修改 ------

pipelineDefault.run({
  // 测试
  stage('Test') {
      def stageBranchs = ['dev'];
      if (false == stageBranchs.contains(env.GIT_BRANCH)) {
        currentBuild.result = 'SUCCESS'
        return
      }

      sh '''
        echo "在这里编写：测试任务脚本（注意环境）"

        dind-notify-dingtalk -a "${DINGTALK_ACCESS_TOKEN}" -m "${DINGTALK_MOBILES}" -t "$(dind-notify-text -t verify-jenkins-access)"
      '''
  }

  // 构建：开发环境
  stage('Build-dev') {
      def stageBranchs = ['dev'];
      if (false == stageBranchs.contains(env.GIT_BRANCH)) {
        currentBuild.result = 'SUCCESS'
        return
      }

      sh '''
        echo "在这里编写：构建任务脚本（注意环境）"

        dind-notify-dingtalk -a "${DINGTALK_ACCESS_TOKEN}" -m "${DINGTALK_MOBILES}" -t "$(dind-notify-text -t verify-jenkins-access)"
      '''
  }

  // 部署：开发环境
  stage('Deploy-dev') {
      def stageBranchs = ['dev'];
      if (false == stageBranchs.contains(env.GIT_BRANCH)) {
        currentBuild.result = 'SUCCESS'
        return
      }

      sh '''
        echo "在这里编写：部署任务脚本（注意环境）"

        dind-notify-dingtalk -a "${DINGTALK_ACCESS_TOKEN}" -m "${DINGTALK_MOBILES}" -t "$(dind-notify-text -t verify-jenkins-access)"
      '''
  }

  // 构建：预发环境
  stage('Build-release') {
      def stageBranchs = ['release'];
      if (false == stageBranchs.contains(env.GIT_BRANCH)) {
        currentBuild.result = 'SUCCESS'
        return
      }

      sh '''
        echo "在这里编写：部署任务脚本（注意环境）"

        dind-notify-dingtalk -a "${DINGTALK_ACCESS_TOKEN}" -m "${DINGTALK_MOBILES}" -t "$(dind-notify-text -t verify-jenkins-access)"
      '''
  }

  // 部署：预发环境
  stage('Deploy-release') {
      def stageBranchs = ['release'];
      if (false == stageBranchs.contains(env.GIT_BRANCH)) {
        currentBuild.result = 'SUCCESS'
        return
      }

      sh '''
        echo "在这里编写：部署任务脚本（注意环境）"

        dind-notify-dingtalk -a "${DINGTALK_ACCESS_TOKEN}" -m "${DINGTALK_MOBILES}" -t "$(dind-notify-text -t verify-jenkins-access)"
      '''
  }

  // 构建：生产环境
  stage('Build-prod') {
      def stageBranchs = ['master'];
      if (false == stageBranchs.contains(env.GIT_BRANCH)) {
        currentBuild.result = 'SUCCESS'
        return
      }

      sh '''
        echo "在这里编写：部署任务脚本（注意环境）"

        dind-notify-dingtalk -a "${DINGTALK_ACCESS_TOKEN}" -m "${DINGTALK_MOBILES}" -t "$(dind-notify-text -t verify-jenkins-access)"
      '''
  }

  // 部署：生产环境
  stage('Deploy-prod') {
      def stageBranchs = ['master'];
      if (false == stageBranchs.contains(env.GIT_BRANCH)) {
        currentBuild.result = 'SUCCESS'
        return
      }

      sh '''
        echo "在这里编写：部署任务脚本（注意环境）"

        dind-notify-dingtalk -a "${DINGTALK_ACCESS_TOKEN}" -m "${DINGTALK_MOBILES}" -t "$(dind-notify-text -t verify-jenkins-access)"
      '''
  }
});