# **京东云服务器J360 G2 用户手册**

## **前言** 

**摘要**

本手册介绍本服务器的规格信息、硬件操作、服务条款、故障诊断等与维护工作密切相关的内容。

**目标受众**

本手册主要适用于以下人员：
- 技术支持工程师
- 产品维护工程师
建议由具备服务器知识的专业工程师参考本手册进行服务器运维操作。

**符号约定**

在本文中可能出现下列标志，它们所代表的含义如下。

![image](https://user-images.githubusercontent.com/117898035/202653027-28a1827f-bc45-4c24-a614-93eaf6db4609.png)

**变更记录**
|版本 |时间 |变更内容 |
|:----|:----|:----|
|V1.0| 2022-11-14|首版发布|
 
## **正文**
### 1、整机柜介绍	
- #### 简介	
    京东云整机柜是京东云首款全自主研发、低成本、高可靠42U机架式整机柜服务器，采用了标准的19英寸设计，完全融合标准服务器的尺寸，对数据中心环境适配要求更低，极大降低了用户使用门槛。京东 云结合用户的需求及痛点，采用自主创新弹性模块化架构设计，用户可以以搭积木的方式，实现按需定制，快速安装，轻松维护。
    
  以高密度、高效能、低功耗、低成本、易管理、灵活部署等特性，为数据中心提供了新一代开放技术管理方案。

- #### 机柜前视图及后视图	
  ![image](https://user-images.githubusercontent.com/117898035/202659523-c6eafb2d-56b7-41c4-8028-7738222ce62c.png)
  ![image](https://user-images.githubusercontent.com/117898035/202660405-c4e9c100-d5a8-4245-8b16-a717791645cd.png)

- #### 机柜左视图及右视图	
  ![image](https://user-images.githubusercontent.com/117898035/202660757-da0f9fc4-6948-4690-9e53-05291485e804.png)
  ![image](https://user-images.githubusercontent.com/117898035/202660789-1f84feac-e126-4271-8c07-aaab5d8ff081.png)

- #### 机柜俯视图	
  ![image](https://user-images.githubusercontent.com/117898035/202660864-ef9ae17f-3178-4d18-a189-85a34ae6c14d.png)

- #### 机柜下视图	
  ![image](https://user-images.githubusercontent.com/117898035/202660893-29081355-7230-449f-aa44-58cd01c86157.png)
  ![image](https://user-images.githubusercontent.com/117898035/202660960-520a2009-5d65-453c-a6f9-e4efd260f8ca.png) 

### 2、服务器介绍	
- #### 简介
    第二代京东云服务器的设计理念源于京东自有大规模云数据中心的建设和运营经验，基于全新一代英特尔®至强®可扩展处理器设计的一款高端双路机架式服务器。J360 G2是继第一代服务器“微定制”之后，基于内部多样化海量业务需求，以及京东云各行业客户需求，自主研发与深度创新的新一代云服务器基础架构。通过系统架构设计创新、核心部件创新，实现了高效、灵活、高性价比的目标。
- #### 服务器前视图及后视图	
   ![image](https://user-images.githubusercontent.com/117898035/202661120-7257c2cb-bfb2-47be-9703-72b9de7b0f15.png) 
   ![image](https://user-images.githubusercontent.com/117898035/202661177-7d118fee-546b-48d5-bad3-b97f7e5eafb1.png)

- #### 服务器左视图及右视图	
   ![image](https://user-images.githubusercontent.com/117898035/202661249-5b3ac3e1-0b47-47d1-91e4-580157087aff.png)
   ![image](https://user-images.githubusercontent.com/117898035/202661623-833563da-6907-4c40-aa1d-3daf9b5102c9.png)
   
- #### 服务器俯视图	
   ![image](https://user-images.githubusercontent.com/117898035/202661698-306d4950-759d-43cc-aeee-be5dae235dc0.png)

### 3、组件识别	

- #### 前面板	
    - 9LFF硬盘机型（前IO）	
   ![image](https://user-images.githubusercontent.com/117898035/202661853-f56bf797-0622-47e8-9714-d653ffe0d0d2.png)
   ![image](https://user-images.githubusercontent.com/117898035/202661895-a5981a79-f6a4-472d-a2c7-3d4b53800584.png) 

    - 16SFF硬盘机型（前IO）	
    ![image](https://user-images.githubusercontent.com/117898035/202662008-d18d9c49-f967-4798-a7df-08347c6638e5.png)
    ![image](https://user-images.githubusercontent.com/117898035/202662044-0d77a39f-ebbe-471f-a3c8-60fa75e24b71.png)

    - 12LFF硬盘机型（后IO）
    ![image](https://user-images.githubusercontent.com/117898035/202662066-03f65fb6-4b0f-4660-8167-ae3ada5b163e.png)
    ![image](https://user-images.githubusercontent.com/117898035/202663008-75d41579-37b8-4376-b9ff-5ff50b27be8f.png)  

    - 16SFF硬盘机型（后IO）	
    ![image](https://user-images.githubusercontent.com/117898035/202662111-5b5e50eb-3dfa-454c-9200-c11c8a09f2ee.png)
    ![image](https://user-images.githubusercontent.com/117898035/202663114-e719759f-3434-4596-8011-47afeb367a20.png)

- #### 前控板按键与指示灯	
    ![image](https://user-images.githubusercontent.com/117898035/202663478-4c5fadde-435a-4278-8511-ddc7d820ca08.png)
    ![image](https://user-images.githubusercontent.com/117898035/202663571-777fc3a9-c05c-4846-b0e5-6cf28f8e9c24.png)

- #### 后面板	
    - 标准电源服务器（前IO）
    ![image](https://user-images.githubusercontent.com/117898035/202663794-9b254709-c00f-4ea1-a6a5-717687b80f98.png)
    ![image](https://user-images.githubusercontent.com/117898035/202663835-c8dd9f4a-1f85-415c-abaa-1d7e99bbdbe2.png)

    - 标准电源服务器（后IO）	
    ![image](https://user-images.githubusercontent.com/117898035/202663853-8787ce41-f5ee-44b9-bd13-89c52f1938fa.png)
    ![image](https://user-images.githubusercontent.com/117898035/202663883-79dc4626-3e99-4da5-93e3-67398e22fda5.png)

    - 整机柜节点服务器（前IO）	
    ![image](https://user-images.githubusercontent.com/117898035/202663919-15b5d60d-beaf-46e2-bd8d-67098593add7.png)
    ![image](https://user-images.githubusercontent.com/117898035/202663951-7cf93c0b-8461-4039-ba1d-9c5933f2732b.png)

- #### 主板布局	
    - 前 I/O 机型主板	
    
    ![image](https://user-images.githubusercontent.com/117898035/202665358-dedd866a-a9a5-42e9-bb5f-9c1aee275985.png)
    ![image](https://user-images.githubusercontent.com/117898035/202665493-4f63b5b0-2962-424e-85ce-6e1ee20e63ff.png)

    - 后 I/O 机型主板	
    
    ![image](https://user-images.githubusercontent.com/117898035/202665852-7dfd1b27-1b15-474a-87ee-8fc9e7fe898d.png)
    ![image](https://user-images.githubusercontent.com/117898035/202665969-64fa9bfb-7bad-4d1c-8f7a-856a6bde4e16.png)

- ####  硬盘编号	
    - 9LFF 硬盘机型	
    硬盘盘位顺序见下图（编号 0—8）。
    ![image](https://user-images.githubusercontent.com/117898035/202666043-59fd47ee-5644-4e90-ab76-aec0b729fadb.png)

    - 12LFF 硬盘机型
    硬盘盘位顺序见下图（编号0—11）。
    ![image](https://user-images.githubusercontent.com/117898035/202666139-c2909cd9-7983-4a70-b5b1-d7128c93e628.png)

    - 16SFF 硬盘机型	
    硬盘盘位顺序见下图（编号0—15）。
    ![image](https://user-images.githubusercontent.com/117898035/202666307-78326a80-9b54-49ea-a71f-e751b9e7c4e7.png)

- #### 硬盘指示灯	
    ![image](https://user-images.githubusercontent.com/117898035/202668309-fd0b11cc-43f7-47b0-9406-da2ca729610e.png)
    ![image](https://user-images.githubusercontent.com/117898035/202668344-f3f1542d-ad0d-4791-aac4-57a8a25887b4.png)

###  4、服务器操作	
- #### 启动服务器	
   在连接到输入电源时，服务器进行短暂自检（电源状态 LED 快速闪烁）后，进入待机状态（电源状态 LED 每秒闪烁一次）。
您可以通过以下任何一种方式开启服务器（电源 LED 点亮）：
  - 按下并释放服务器前控制板上的电源按钮，启动服务器。
  - 启动BMC网路界面：登录BMC网路界面，从电源控制操作列表框选择启动。
  - 登录BMC CLI，发出IPMI命令，以启动系统。

![image](https://user-images.githubusercontent.com/117898035/202671378-2513f032-8d8c-4dfa-b396-a9e371aa5187.png)

**如果引导屏幕上持续显示“系统安全 - 系统受损”消息，则意味着未正确安装服务器外盖。请将其卸下并重新装回，然后重新启动服务器。**


- #### 关闭服务器	
   

- #### 将服务器从机架中拉出	


- #### 取下主机上盖	

- #### 安装主机上盖	


- #### 卸下PCIe Riser卡笼	


- #### 安装PCIE Riser卡笼	


- ####	安装前置 PCIe 模组	


- ####	安装内置 PCIe 模组


- ####	安装后置 PCIe 模组	

- #### 卸下导风罩	

- #### 安装导风罩	

- #### 移除风扇模组	

- #### 安装风扇模组	



