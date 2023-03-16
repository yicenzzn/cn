

# PC JRTC API概览

#### 一、模块说明

​        JRTCElectronSDK模块是node的c++原生模块，是对JRTCSDK的node封装。可由Javascript直接调用，接口说明参见doc目录下的文档。JRTCElectronSDK模块提供了进入会议、打开/关闭本地视频、打开/关闭远程视频、桌面共享、获取摄像头列表、获取麦克风列表、获取扬声器列表、渲染等功能。

#### 二、目录说明

```shell
JRTCElectronSDK
|-- build           存放生成JRTCElectronSDK模块在不同平台下的解决方案文件及编译后输出文件的目录
|-- doc             存放JRTCElectronSDK模块的API说明文档的目录
|-- examples        存放测试JRTCElectronSDK模块的demo目录
|-- include         存放第三方库的头文件目录
|-- lib             存放第三方库的lib、dll文件的目录
|-- src             存放源文件的目录
|-- binding.gyp     平台工程生成文件
|-- package.json    打包配置文件
|-- readme.md       JRTCElectronSDK模块说明文件
```

#### 三、环境要求

- JRTCElectronSDK模块需要安装node.js(x64 v16.2.0)
- 验证node.js是否安装成功：`node -v `    `npm -v`

#### 四、JRTCElectronSDK模块编译与打包

进入JRTCElectronSDK目录

- 编译命令

```cmd
node-gyp clean configure build --verbose --arch=x64
```

- 打包命令

```cmd
npm pack
```

命令执行成功后会在JRTCElectronSDK目录下生成JRTCElectronSDK-1.0.0.tgz文件

#### 五、JRTCElectronSDK模块安装与卸载

- 插件安装

在Electron程序目录中执行下面命令可以将JRTCElectronSDK模块安装到该程序目录中

```cmd
npm install ../../JRTCElectronSDK-1.0.0.tgz
```

插件中examples目录中已经提供了ElectronDemo程序，可以先从JRTCElectronSDK-1.0.0.tgz安装包中提取到JRTCElectronDemo程序，然后进入到JRTCElectronDemo目录中并将JRTCElectronSDK-1.0.0.tgz文件拷贝到JRTCElectronDemom目录中。安装JRTCElectronSDK模块，命令如下：

```cmd
cd JRTCElectronDemo
npm install ./JRTCElectronSDK-1.0.0.tgz
```

- 插件卸载

```cmd
cd JRTCElectronDemo
npm uninstall JRTCElectronSDK
```

- electron的版本可能与插件的版本不一致，安装插件后可重新编译electron

```cmd
npm install --save-dev electron-rebuild
npm install 
./node_modules/.bin/electron-rebuild.cmd
```

#### 六、渲染插件安装

渲染需要依赖yuv-canvas、yuv-buffer、lodash.isequal三个插件，安装插件命令如下：

```cmd
npm install yuv-canvas
npm install yuv-buffer
npm install lodash.isequal
```

目前该安装包已经配置到了安装文件中，无需单独安装。

#### 七、JRTCElectronSDK模块API文档生成

```cmd
cd JRTCElectronSDK\src\js\Api
jsdoc index.js Listener.js -d ../../../doc
```

#### 八、接口测试说明

1.会议参数获取

- 启动JRTCElectronDemo程序后会出现进入会议界面,需要填入会议信息
- 会议号、参会者ID、参会者昵称、会议touken、会议appId、会议userId、会议nonce的值可以通过京东会议客户端的日志中获取
- 在京东会议PC端的安装目录下找到jrtc_logs目录，打开该目录下的日志文件，搜索"joinRoom request:"即可获取进入会议所需信息，注意：搜索日志前需要先用PC端进入一下会议才会有日志输出

2.功能点测试：

- 打开/关闭本地视频 —— 操作：点击"打开/关闭本地视频"按钮
- 打开/关闭本地音频 —— 操作：点击"打开/关闭本地音频"按钮
- 开始屏幕共享 —— 操作：点击”开始共享屏幕“按钮 =》出现屏幕及应用程序画面预览 =》选中应用程序或屏幕 =》点击应用程序或画面上方的"确认选择"按钮 =》屏幕及应用程序画面关闭，屏幕共享完成(可用其他端查看验证)
- 停止屏幕共享 —— 操作：点击”停止屏幕共享“按钮 =》 屏幕共享结束
- 更新用户昵称 —— 操作：在输入框中输入昵称 =》点击”更新用户昵称按钮” =》用户昵称更新完成(可用其他端查看验证)
- 获取摄像头列表 ——  操作：点击”获取摄像头列表“按钮 =》右边显示框中显示当前设备可用的摄像头列表
- 获取扬声器列表 ——  操作：点击”获取扬声器列表“按钮 =》右边显示框中显示当前设备可用的扬声器列表
- 获取麦克风列表 ——  操作：点击”获取麦克风列表“按钮 =》右边显示框中显示当前设备可用的麦克风列表
- 发送消息 —— 操作：先开启远程用户视频 =》选中一个远程用户的视频窗口 =》在输入框中输入要发送的消息 =》点击"发送消息"按钮 =》 消息发送成功(可用其他端查看验证)
- 暂停/恢复本地视频 —— 操作：勾选/取消勾选"暂停远程视频"按钮 =》画面暂停/恢复
- 暂停/恢复本地音频 ——操作：勾选/取消勾选"暂停远程音频"按钮 =》音频暂停/恢复
- 暂停/恢复远程视频 —— 操作：先开启远程用户视频 =》选中一个远程用户的视频窗口 =》勾选/取消勾选"暂停远程视频"按钮  =》画面暂停/恢复
