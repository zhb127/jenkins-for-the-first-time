// - 钉钉通知相关配置项
env.DIND_NOTIFY_DINGTALK_ACCESS_TOKEN="c44ba5e19146b35c79ed092cbb3562d8038ab6733fd1094c9ce730bfd82a9874"; // 钉钉群机器人 access-token
env.DIND_NOTIFY_DINGTALK_MOBILES="";      // at 指定人员，值格式为：手机号,手机号,手机号；at 所有人，值为：all

pipelineDefault.run({
  // 测试
  stage('Test') {
    when(['dev'].contains(env.BRANCH_NAME)) {
      sh '''
        echo "在这里编写：测试任务脚本（注意环境）"
      '''
    }
  }

  // 构建：开发环境
  stage('Build-dev') {
    when(['dev'].contains(env.BRANCH_NAME)) {
      sh '''
        echo "在这里编写：构建任务脚本（注意环境）"
      '''
    }
  }

  // 部署：开发环境
  stage('Deploy-dev') {
    when(['dev'].contains(env.BRANCH_NAME)) {
      sh '''
        echo "在这里编写：部署任务脚本（注意环境）"
      '''
    }
  }

  // 构建：预发环境
  stage('Build-release') {
    when(['release'].contains(env.BRANCH_NAME)) {
      sh '''
        echo "在这里编写：构建任务脚本（注意环境）"
      '''
    }
  }

  // 部署：预发环境
  stage('Deploy-release') {
    when(['release'].contains(env.BRANCH_NAME)) {
      sh '''
        echo "在这里编写：部署任务脚本（注意环境）"
      '''
    }
  }

  // 构建：生产环境
  stage('Build-prod') {
    when(['master'].contains(env.BRANCH_NAME)) {
      sh '''
        echo "在这里编写：构建任务脚本（注意环境）"
      '''
    }
  }

  // 部署：生产环境
  stage('Deploy-prod') {
    when(['master'].contains(env.BRANCH_NAME)) {
      sh '''
        echo "在这里编写：部署任务脚本（注意环境）"
      '''
    }
  }
});