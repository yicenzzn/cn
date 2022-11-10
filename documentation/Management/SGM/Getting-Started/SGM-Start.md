# 为Java应用快速安装探针

SGM提供一键接入方式为Java应用安装探针，安装成功后只需重启应用即可进入SGM开始监控。当应用重启时，探针会自动加载，该Java应用将自动接入SGM应用监控。

## 前提条件

- 检查您的JDK版本。SGM应用监控支持的JDK版本如下：

    - JDK 1.6.0+
    - JDK 1.7.0+
    - JDK 1.8.0_60+
      **说明**
        - 建议使用1.8.X最新版本，最后一个免费版本为1.8.0_202。
    - JDK 11.0.0+

- 申请ak、sk

## 操作步骤

### tomcat
1. 在{TOMCAT_HOME}/bin/setenv.sh文件中添加以下配置
```
#!/bin/bash
SGM_APP_NAME="${AppName}"
SGM_PROBE_AK="${ak}"
SGM_PROBE_SK="${sk}"
SGM_PROBE_ZONE="${zone}"
#存放sgm探针的本地目录,进程启动用户需要有写权限
SGM_PROBE_BASEDIR="/export/servers/sgm-probe-java"
#SGM服务地址
SGM_SERVER_ADDRESS="${sgm_server_address}"
#SGM探针包下载地址
SGM_PROBE_DOWNLOAD="${sgm_probe_address}"
curl -s "$SGM_PROBE_DOWNLOAD/install.sh" -o /tmp/sgm_java.sh && source /tmp/sgm_java.sh
export CATALINA_OPTS="$CATALINA_OPTS $SGM_OPTS"
```

**说明**
- 将`${AppName}`替换成您的应用名，应用名暂不支持中文。
- 将`${ak}`替换成您的ak，`${sk}`换成您的sk。
- 将`${zone}`替换成您应用所在的地域，华北:cn-north-1，华南:cn-south-1，华东:cn-east-2。
- 将`${sgm_server_address}`替换成您应用所在地域的SGM服务地址，华北:http://sgm-cn-north-1.jdcloud.com，华南:http://sgm-cn-south-1.jdcloud.com，华东:http://sgm-cn-east-2.jdcloud.com。
- 将`${sgm_probe_address}`替换成您应用所在地域的SGM针包下载地址，华北:https://static-resources.s3-internal.cn-north-1.jdcloud-oss.com/sgm/cloud，华南:https://static-resources-hn.s3.cn-south-1.jdcloud-oss.com/sgm/cloud，华东:https://static-resources-sh.s3.cn-east-2.jdcloud-oss.com/sgm/cloud。
- 执行安装脚本后，该脚本会自动下载最新探针。

2. 重启应用

### SpringBoot
1. 请在启动脚本start.sh之前加入脚本
```
#!/bin/bash
SGM_APP_NAME="${AppName}"
SGM_PROBE_AK="${ak}"
SGM_PROBE_SK="${sk}"
SGM_PROBE_ZONE="${zone}"
#存放sgm探针的本地目录,进程启动用户需要有写权限
SGM_PROBE_BASEDIR="/export/servers/sgm-probe-java"
#SGM服务地址
SGM_SERVER_ADDRESS="${sgm_server_address}"
#SGM探针包下载地址
SGM_PROBE_DOWNLOAD="${sgm_probe_address}"
curl -s "$SGM_PROBE_DOWNLOAD/install.sh" -o /tmp/sgm_java.sh && source /tmp/sgm_java.sh
```

**说明**
- 将`${AppName}`替换成您的应用名，应用名暂不支持中文。
- 将`${ak}`替换成您的ak，`${sk}`换成您的sk。
- 将`${zone}`替换成您应用所在的地域，华北:cn-north-1，华南:cn-south-1，华东:cn-east-2。
- 将`${sgm_server_address}`替换成您应用所在地域的SGM服务地址，华北:http://sgm-cn-north-1.jdcloud.com，华南:http://sgm-cn-south-1.jdcloud.com，华东:http://sgm-cn-east-2.jdcloud.com。
- 将`${sgm_probe_address}`替换成您应用所在地域的SGM针包下载地址，华北:https://static-resources.s3-internal.cn-north-1.jdcloud-oss.com/sgm/cloud，华南:https://static-resources-hn.s3.cn-south-1.jdcloud-oss.com/sgm/cloud，华东:https://static-resources-sh.s3.cn-east-2.jdcloud-oss.com/sgm/cloud。
- 执行安装脚本后，该脚本会自动下载最新探针。

2. 在应用启动命令中加入$SGM_OPTS, 例如: java $SGM_OPTS -jar /export/package/springboot-sample/lib/sample.jar

3. 重启应用

## 结果验证

约一分钟后，若您的应用出现在我的应用中，则说明接入成功。

## 卸载探针

### tomcat

1. 删除在{TOMCAT_HOME}/bin/setenv.sh中SGM的脚本。

2. 重启您的应用。

### SpringBoot

1. 删除启动脚本start.sh中SGM的脚本。

2. 删除启动命令中的$SGM_OPTS。

3. 重启您的应用。

## 常见问题

### 启动死锁
如果应用使用的tomcat版本在8.0.0-8.0.31之间，请升级tomcat版本到8.0.32及以上 或者 降到tomcat 6，tomcat7，否则有几率会导致启动时死锁。
默写带有自定义classloader的应用，可能会在自动发现监控阶段发生死锁，可以通过参数关闭自动发现功能

### 启动脚本添加正确，但在sgm界面的应用列表看不到接入应用
请确认启动日志中有类似"find app name"这样的日志，保证探针发现了应用名，如果有“can not find app name“这样的日志，代表没有探针没有发现应用名

### 无法监控dubbo类型的调用，其他类型的调用没问题
不要引入了saf.jar，否则会造成dubbo框架不能加载Filter

### 不能自动发现监控，且调用链无法连接
不要使用dom4j1.6.1以下的版本，不要依赖了pull-parser
dom4j低版本有xml冲突，phoneix-hbase会强转线程池中runnable

### 关于JDK8早期版本运行lambda异常crash问题
升级JDK小版本到1.8.0_60以上

### 关于使用了itext-asian的jar之后系统有时无法正常启动的问题
请不要使用itext-asian的jar包