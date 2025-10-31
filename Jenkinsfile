pipeline {
    agent any
    
    parameters {
        choice(
            name: 'DEPLOY_ENV',
            choices: ['dev', 'staging', 'prod'],
            description: '选择部署环境'
        )
        booleanParam(
            name: 'RUN_TESTS', 
            defaultValue: true, 
            description: '是否运行测试'
        )
        string(
            name: 'VERSION',
            defaultValue: '1.0.0',
            description: '输入版本号'
        )
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo '✅ 开始从GitHub拉取代码...'
                checkout scm
            }
        }
        stage('Install & Test') {
            steps {
                echo '🔧 安装依赖和运行测试...'
                sh 'npm test'
            }
        }
        stage('Build') {
            steps {
                echo '🏗️ 构建应用...'
                sh 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                echo '🚀 部署准备就绪...'
                echo '这里是部署阶段，可以添加真实的部署脚本'
            }
        }
    }
    post {
        always {
            echo '📧 发送通知...'
            echo '构建完成！'
        }
        success {
            echo '🎉 自动化构建成功！'
        }
    }
}
