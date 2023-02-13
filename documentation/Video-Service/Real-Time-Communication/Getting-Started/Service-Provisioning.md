# 接入流程

1.右上角，控制台-注册/登录（支持京东账号登录）。  
![image](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/%E5%BC%80%E9%80%9A%E6%9C%8D%E5%8A%A1-1.png)

2.控制台-云服务-搜索“音视频通信”，点击进入。    
![image](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/%E5%BC%80%E9%80%9A%E6%9C%8D%E5%8A%A1-2.png)

3.勾选同意协议，开通服务。   
![image](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/%E5%BC%80%E9%80%9A%E6%9C%8D%E5%8A%A1-3.png)
 
4.开通jrtc服务后，进入应用管理页面，维护应用，获取appId 和appKey![Uploading image.png…]

5.维护和获取访问京东云API的密钥Access Key ID和Access Key Secret![image]
![image](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/Key.png)
![image](https://github.com/jdcloudcom/cn/blob/cn-Real-Time-Communication/image/Real-Time-Communicat/Key.png)

6.引入依赖调用openapi
<!-- https://mvnrepository.com/artifact/com.jdcloud.sdk/openjrtc -->
<dependency>
    <groupId>com.jdcloud.sdk</groupId>
    <artifactId>openjrtc</artifactId>
    <version>1.1.8</version>
</dependency>

7.接口概览
https://docs.jdcloud.com/cn/real-time-communication/api/overview?content=API

8.调用方式
公有云用户调用方式 
 public void jrtcDemo() {
    OpenjrtcClient client = OpenjrtcClient
            .builder()
            .credentialsProvider(new StaticCredentialsProvider("Access Key ID", "Access Key Secret"))
            .httpRequestConfig(new HttpRequestConfig.Builder().protocol(Protocol.HTTP).build())
            .build();
 
    //注册用户
    RegisterUserRequest request = new RegisterUserRequest();
    request.setAppId("控制台创建");
    request.setTemporary(false);
    request.setUserId("自定义");
    request.setUserName("自定义");
    RegisterUserResponse userResp = client.registerUser(request);
 
    //注册房间
    RegisterUserRoomRequest roomRequest = new RegisterUserRoomRequest();
    roomRequest.setAppId("控制台创建");
    roomRequest.setUserRoomId("自定义");
    roomRequest.setRoomName("自定义");
    // roomType 1-小房间 2-大房间  不设置默认去app的roomType类型
    roomRequest.setRoomType(2);
    RegisterUserRoomResponse roomResp = client.registerUserRoom(roomRequest);
![image](https://user-images.githubusercontent.com/115534646/218384490-40da0808-a0ff-4b65-8be8-d5b9721605c2.png)


