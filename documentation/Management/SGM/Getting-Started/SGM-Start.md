# 为Java应用快速安装探针

SGM提供一键接入方式为Java应用安装探针，安装成功后只需重启应用即可开始监控。当应用重启时，探针会自动加载，该Java应用将自动接入SGM应用监控。

## 前提条件

- 检查您的JDK版本。SGM应用监控支持的JDK版本如下：

    - JDK 1.6.0+
    - JDK 1.7.0+
    - JDK 1.8.0_60+
      **说明**
        - 建议使用1.8.X最新版本，最后一个免费版本为1.8.0_202。
    - JDK 11.0.0+

- [申请accessKeyId、secretAccessKey](https://uc.jdcloud.com/account/accesskey)

## 操作步骤

### tomcat
1. 在{TOMCAT_HOME}/bin/setenv.sh文件中添加以下配置
```
#!/bin/bash
#应用名（必填）
SGM_APP_NAME="${AppName}"
#accessKeyId（必填）
SGM_PROBE_AK="${accessKeyId}"
#secretAccessKey（必填）
SGM_PROBE_SK="${secretAccessKey}"
#存放sgm探针的本地目录,进程启动用户需要有写权限（选填）
SGM_PROBE_BASEDIR="/export/servers/sgm-probe-java"
#SGM探针包下载地址（不可修改）
SGM_PROBE_DOWNLOAD="https://static-resources.s3.cn-north-1.jdcloud-oss.com/sgm/cloud"
curl -s "$SGM_PROBE_DOWNLOAD/install.sh" -o /tmp/sgm_java.sh && source /tmp/sgm_java.sh
export CATALINA_OPTS="$CATALINA_OPTS $SGM_OPTS"
```

**说明**
- 将`${AppName}`替换成您的应用名，应用名暂不支持中文。
- 将`${accessKeyId}`替换成您的accessKeyId，`${secretAccessKey}`换成您的secretAccessKey。
- 执行安装脚本后，该脚本会自动下载最新探针。

2. 重启应用

### SpringBoot
1. 请在启动脚本start.sh最前面加入以下脚本
```
#!/bin/bash
#应用名（必填）
SGM_APP_NAME="${AppName}"
#accessKeyId（必填）
SGM_PROBE_AK="${accessKeyId}"
#secretAccessKey（必填）
SGM_PROBE_SK="${secretAccessKey}"
#存放sgm探针的本地目录,进程启动用户需要有写权限（选填）
SGM_PROBE_BASEDIR="/export/servers/sgm-probe-java"
#SGM探针包下载地址（不可修改）
SGM_PROBE_DOWNLOAD="https://static-resources.s3.cn-north-1.jdcloud-oss.com/sgm/cloud"
curl -s "$SGM_PROBE_DOWNLOAD/install.sh" -o /tmp/sgm_java.sh && source /tmp/sgm_java.sh
```

**说明**
- 将`${AppName}`替换成您的应用名，应用名暂不支持中文。
- 将`${accessKeyId}`替换成您的accessKeyId，`${secretAccessKey}`换成您的secretAccessKey。
- 执行安装脚本后，该脚本会自动下载最新探针。

2. 在应用启动命令中加入$SGM_OPTS, 例如: java $SGM_OPTS -jar /export/package/springboot-sample/lib/sample.jar

3. 重启应用

## 结果验证

约一分钟后，若您的应用出现在菜单[我的应用]中，则说明接入成功。

## 卸载探针

### tomcat

1. 删除在{TOMCAT_HOME}/bin/setenv.sh中SGM的脚本。

2. 重启您的应用。

### SpringBoot

1. 删除启动脚本start.sh中SGM的脚本。

2. 删除启动命令中的$SGM_OPTS。

3. 重启您的应用。

## 常见问题

### 接入后如何验证接入成功了？
1. 首先，通过ps命令查看进程（ps -ef | grep 'sgm'），确认进程里有 -javaagent 关键字，如：-javaagent:/export/servers/sgm-probe-java/sgm-probe-5.4.0-ex/sgm-agent-5.4.0.jar

2. 其次，登陆SGM管理端页面，进入我的应用，可以看到刚才接入的应用，同时监控数大于0。

3. 最后在业务产生调用后，可以在应用监控->方法调用查询输入对应的应用名可以查到调用日志，则说明接入成功。

### 接入成功后为什么控制台上没有监控数据？
1. 请确认您的应用是否发送调用请求，同时确认开发框架是否在SGM支持范围内。

2. 检查JDK版本。如果JDK版本在1.8.0_60以下，可能会出现无法安装Agent的情况，请您升级JDK版本，建议使用1.8.X最新版本，最后一个免费版本为1.8.0_202。 
   
3. SGM Agent日志会打印在控制台日志中（如console.log），请查看您的控制台日志是否有报错。
   
4. 如果SGM Agent日志中的报错无法自行解决，请将其保存为压缩文件，并联系客服。