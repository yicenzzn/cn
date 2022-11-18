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
#### 简介
- 京东云整机柜是京东云首款全自主研发、低成本、高可靠 42U 机架式整机柜服务器，采用了标准的 19 英寸设计，完全融合标准服务器的尺寸，对数据中心环境适配要求更低，极大降低了用户使用门槛。京东云结合用户的需求及痛点，采用自主创新弹性模块化架构设计，用户可以以搭积木的方式，实现按需定制，快速安装，轻松维护。   
- 以高密度、高效能、低功耗、低成本、易管理、灵活部署等特性，为数据中心提供了新一代开放技术管理方案。

#### 机柜前视图及后视图	
  ![image](https://user-images.githubusercontent.com/117898035/202659523-c6eafb2d-56b7-41c4-8028-7738222ce62c.png)
  ![image](https://user-images.githubusercontent.com/117898035/202660405-c4e9c100-d5a8-4245-8b16-a717791645cd.png)

#### 机柜左视图及右视图	
  ![image](https://user-images.githubusercontent.com/117898035/202660757-da0f9fc4-6948-4690-9e53-05291485e804.png)
  ![image](https://user-images.githubusercontent.com/117898035/202660789-1f84feac-e126-4271-8c07-aaab5d8ff081.png)

#### 机柜俯视图	
  ![image](https://user-images.githubusercontent.com/117898035/202660864-ef9ae17f-3178-4d18-a189-85a34ae6c14d.png)

#### 机柜下视图	
  ![image](https://user-images.githubusercontent.com/117898035/202660893-29081355-7230-449f-aa44-58cd01c86157.png)
  ![image](https://user-images.githubusercontent.com/117898035/202660960-520a2009-5d65-453c-a6f9-e4efd260f8ca.png) 

### 2、服务器介绍
#### 简介
- 第二代京东云服务器的设计理念源于京东自有大规模云数据中心的建设和运营经验，基于全新一代英特尔®至强®可扩展处理器设计的一款高端双路机架式服务器。J360 G2是继第一代服务器“微定制”之后，基于内部多样化海量业务需求，以及京东云各行业客户需求，自主研发与深度创新的新一代云服务器基础架构。
- 通过系统架构设计创新、核心部件创新，实现了高效、灵活、高性价比的目标。
    
#### 服务器前视图及后视图	
   ![image](https://user-images.githubusercontent.com/117898035/202661120-7257c2cb-bfb2-47be-9703-72b9de7b0f15.png) 
   ![image](https://user-images.githubusercontent.com/117898035/202661177-7d118fee-546b-48d5-bad3-b97f7e5eafb1.png)

#### 服务器左视图及右视图	
   ![image](https://user-images.githubusercontent.com/117898035/202661249-5b3ac3e1-0b47-47d1-91e4-580157087aff.png)
   ![image](https://user-images.githubusercontent.com/117898035/202661623-833563da-6907-4c40-aa1d-3daf9b5102c9.png)
   
#### 服务器俯视图	
   ![image](https://user-images.githubusercontent.com/117898035/202661698-306d4950-759d-43cc-aeee-be5dae235dc0.png)

### 3、组件识别	

#### 前面板	
- **9LFF 硬盘机型（前 I/O）**	
   ![image](https://user-images.githubusercontent.com/117898035/202661853-f56bf797-0622-47e8-9714-d653ffe0d0d2.png)
   ![image](https://user-images.githubusercontent.com/117898035/202661895-a5981a79-f6a4-472d-a2c7-3d4b53800584.png) 
   
- **16SFF 硬盘机型（前 I/O）**	
    ![image](https://user-images.githubusercontent.com/117898035/202662008-d18d9c49-f967-4798-a7df-08347c6638e5.png)
    ![image](https://user-images.githubusercontent.com/117898035/202662044-0d77a39f-ebbe-471f-a3c8-60fa75e24b71.png)

- **12LFF 硬盘机型（后 I/O）**
    ![image](https://user-images.githubusercontent.com/117898035/202662066-03f65fb6-4b0f-4660-8167-ae3ada5b163e.png)
    ![image](https://user-images.githubusercontent.com/117898035/202663008-75d41579-37b8-4376-b9ff-5ff50b27be8f.png)  

- **16SFF 硬盘机型（后 I/O）**	
    ![image](https://user-images.githubusercontent.com/117898035/202662111-5b5e50eb-3dfa-454c-9200-c11c8a09f2ee.png)
    ![image](https://user-images.githubusercontent.com/117898035/202663114-e719759f-3434-4596-8011-47afeb367a20.png)

#### 前控板按键与指示灯	

    前控板按键与指示灯
    
    ![image](https://user-images.githubusercontent.com/117898035/202689015-7da8fe8e-f49d-4a7b-bfd2-2c14e9861fe1.png)
    
    ![image](https://user-images.githubusercontent.com/117898035/202689060-7d18f91e-906c-46dc-821c-9ccad1b5004c.png)

#### 后面板	
- **标准电源服务器（前 I/O）**
    ![image](https://user-images.githubusercontent.com/117898035/202663794-9b254709-c00f-4ea1-a6a5-717687b80f98.png)
    ![image](https://user-images.githubusercontent.com/117898035/202663835-c8dd9f4a-1f85-415c-abaa-1d7e99bbdbe2.png)

- **标准电源服务器（后 I/O）**	
    ![image](https://user-images.githubusercontent.com/117898035/202663853-8787ce41-f5ee-44b9-bd13-89c52f1938fa.png)
    ![image](https://user-images.githubusercontent.com/117898035/202663883-79dc4626-3e99-4da5-93e3-67398e22fda5.png)

- **整机柜节点服务器（前 I/O）**	
    ![image](https://user-images.githubusercontent.com/117898035/202663919-15b5d60d-beaf-46e2-bd8d-67098593add7.png)  
    ![image](https://user-images.githubusercontent.com/117898035/202663951-7cf93c0b-8461-4039-ba1d-9c5933f2732b.png)

#### 主板布局	
- **前 I/O 机型主板**  
    ![image](https://user-images.githubusercontent.com/117898035/202665358-dedd866a-a9a5-42e9-bb5f-9c1aee275985.png)  
    ![image](https://user-images.githubusercontent.com/117898035/202665493-4f63b5b0-2962-424e-85ce-6e1ee20e63ff.png)

- **后 I/O 机型主板**    
    ![image](https://user-images.githubusercontent.com/117898035/202665852-7dfd1b27-1b15-474a-87ee-8fc9e7fe898d.png)  
    ![image](https://user-images.githubusercontent.com/117898035/202665969-64fa9bfb-7bad-4d1c-8f7a-856a6bde4e16.png)

####  硬盘编号	
- **9LFF 硬盘机型**
    硬盘盘位顺序见下图（编号 0—8）。 
    ![image](https://user-images.githubusercontent.com/117898035/202666043-59fd47ee-5644-4e90-ab76-aec0b729fadb.png)

- **12LFF 硬盘机型**
    硬盘盘位顺序见下图（编号0—11）。
    ![image](https://user-images.githubusercontent.com/117898035/202666139-c2909cd9-7983-4a70-b5b1-d7128c93e628.png)

- **16SFF 硬盘机型**	
    硬盘盘位顺序见下图（编号0—15）。
    ![image](https://user-images.githubusercontent.com/117898035/202666307-78326a80-9b54-49ea-a71f-e751b9e7c4e7.png)

#### 硬盘指示灯	

   ![image](https://user-images.githubusercontent.com/117898035/202689372-f4b16a2c-d208-4ce6-8f73-32af4d7efd0f.png)
   
   ![image](https://user-images.githubusercontent.com/117898035/202689411-540657f6-eb95-4b40-97df-d8640dc2f921.png)

###  4、服务器操作	
#### 启动服务器	
   在连接到输入电源时，服务器进行短暂自检（电源状态 LED 快速闪烁）后，进入待机状态（电源状态 LED 每秒闪烁一次）。
您可以通过以下任何一种方式开启服务器（电源 LED 点亮）：
   - 按下并释放服务器前控制板上的电源按钮，启动服务器。
   - 启动BMC网路界面：登录BMC网路界面，从电源控制操作列表框选择启动。
   - 登录BMC CLI，发出IPMI命令，以启动系统。

![image](https://user-images.githubusercontent.com/117898035/202671378-2513f032-8d8c-4dfa-b396-a9e371aa5187.png)

 如果引导屏幕上持续显示“系统安全 - 系统受损”消息，则意味着未正确安装服务器外盖。请将其卸下并重新装回，然后重新启动服务器。


#### 关闭服务器	
   ![image](https://user-images.githubusercontent.com/117898035/202671532-9cc6d796-3535-45cd-84c0-b393fa306147.png)
为减少人身伤害、电击或设备损坏的危险，请拔出电源线插头以断开服务器电源。前面板的 “电源开关按键”按钮不能彻底切断系统电源。在切断交流电源前，部分电源和一些内部电路仍带电。

 要将服务器置于待机状态（打开电源 LED 每秒闪烁一次）：
  - 使用操作系统开始正常关闭（如果操作系统支持）。
  - 按下“打开电源”按钮开始正常关闭（如果操作系统支持）。
  - 登录BMC CLI，发出IPMI命令，以关闭系统。
  - 紧急关闭：按住电源按钮超过 4 秒，进行关机。

![image](https://user-images.githubusercontent.com/117898035/202671754-d7321b58-e644-4f4c-92bc-131198ec789c.png)

 正常关闭：关闭之前，需要储存所有打开的文件和网络服务，关闭所有应用程序，停止或终止所有必要的系统流程，然后才可以进行关机操作。
 紧急关闭：所有应用程序和文件将关闭，不储存更改，文件系统可能损坏。

#### 将服务器从机架中拉出	

![image](https://user-images.githubusercontent.com/117898035/202671817-1a125489-240e-49d0-985c-857bbd7afdf2.png)

 为减少人身伤害或设备损坏的危险，将组件从机架中拉出之前应保证机架足够稳固。

  - 拧松服务器左右挂耳内的松不脱螺钉。
  - 将服务器从机架中拉出。
  
    ![image](https://user-images.githubusercontent.com/117898035/202672061-dfdbf719-44e2-4082-a508-83b9321c4518.png)
    
  - 在执行安装或维护步骤后，将服务器向后推入机架，并固定到位。
  
  ![image](https://user-images.githubusercontent.com/117898035/202672161-6856153c-54bb-4d9f-aa2a-a2d518635f33.png)

#### 取下主机上盖	

  ![image](https://user-images.githubusercontent.com/117898035/202672203-1277be35-edd5-490b-9107-11759c84165e.png)

 为避免设备表面温度过高而造成人身伤害的危险，请在驱动器和内部系统组件散热后再触碰设备。

  ![image](https://user-images.githubusercontent.com/117898035/202672241-c8cde05e-72e1-45ab-a635-f4b7741d0576.png)

 请小心取放顶盖。在外盖滑锁打开的情况下跌落顶盖可能会损坏外盖滑锁。
 为充分散热，请不要在未安装主机上盖、导风罩、风扇的情况下运行服务器。如果服务器支持热插拔组件，请最大限度地减少打开主机上盖的时间。

 卸下组件：
  - 如果执行非热插拔安装或维护步骤，则关闭服务器电源。
  - 将服务器从机架中拉出。
  - 使用螺丝刀拧松机盖锁定器上的安全保护螺钉。
  - 提起机盖锁定器手柄，如下图箭头所示方向，卸下主机上盖。
  
  ![image](https://user-images.githubusercontent.com/117898035/202672516-6496eb23-6107-435b-87f8-59c83059d50b.png)

#### 安装主机上盖	
  - 打开机盖锁定器，将主机上盖对准服务器安装槽位并垂直放下。
  - 将主机上盖滑到闭合位置，向下扣合机盖锁定器。
  - 使用螺丝刀拧紧机盖锁定器上的安全保护螺钉。
  ![image](https://user-images.githubusercontent.com/117898035/202672664-6501236f-bc7e-480a-8121-93cdd9a4641c.png)

#### 卸下 PCIe Riser 卡笼	
  ![image](https://user-images.githubusercontent.com/117898035/202672689-7923c657-4f87-48bf-975b-4c91c8e98518.png)

  为了避免损坏服务器或扩展卡，在拆卸或安装PCIe Riser卡笼之前，应关闭服务器电源并拔出所有交流电源插头。

  按以下信息卸下 PCIe Riser 卡笼。本过程以前置 PCIe Riser 卡笼为例，其他 PCIe Riser 卡笼拆卸方法与此相似。
  
  **步骤**
  - 步骤 1. 解锁前 IO 模块与机箱相连的螺丝，向机箱外抽出前IO 模块。

    ![image](https://user-images.githubusercontent.com/117898035/202672753-6d5f9d06-8b28-4975-bb45-8a06307c6acd.png)
    
  - 步骤 2. 向上提前取出 PCIe 模块。捏住PCIe 适配器的两端然后取出 PCIe 适配器。

    ![image](https://user-images.githubusercontent.com/117898035/202672806-1e324dd6-940c-4b6b-9e36-5057c64d19c5.png)

  - 步骤 3. 解锁固定转接卡的两颗螺丝，向右滑动转接卡然后取出转接卡，分离转接卡和 PCIe 卡支架。

   ![image](https://user-images.githubusercontent.com/117898035/202672834-693d14b7-9f9e-4b10-861a-e75511e92aad.png)


#### 安装 PCIE Riser 卡笼	

- **安装前置 PCIe 模组**
  
  **步骤**
    - 步骤 1. 组装PCIe模组。
      a.将转接卡螺钉孔和葫芦孔与 PCIe 支架上的螺钉孔和立柱对齐，向左滑动。
      b.拧紧两颗螺钉，将转接卡固定在 PCIe 支架上。

      ![image](https://user-images.githubusercontent.com/117898035/202672937-6f91aa7c-03de-48f8-add9-40b515cfd03a.png)

      c.将 PCIe 适配器对齐转接卡上的插槽，然后轻轻地按压 PCIe 适配器的两端，直到适配器在插槽上牢固就位。
      d.将装有 PCIe 适配器的支架向下插入到 OCP 支架上，组成 PCIe 模组。
     
      ![image](https://user-images.githubusercontent.com/117898035/202672973-e63aeaeb-6ba1-42d2-a355-255004f5d9f2.png)
      
   - 步骤 2. 将线缆连接到转接卡上。
   - 步骤 3. 安装 PCIe 模组。
       a. 将线材穿过硬盘仓，伸到机箱内部，把 PCIe 模组插入硬盘仓，并向机箱背面推动。
       b. 锁紧两颗自带螺钉固定 PCIe 模组。

       ![image](https://user-images.githubusercontent.com/117898035/202673010-ba09aaa3-aba1-4c28-992d-ca535b8275aa.png)

- **安装内置 PCIe 模组**
 
  **步骤**
    - 步骤 1. 安装转接卡。
       a.将转接卡螺钉孔和葫芦孔与 PCIe 支架上的螺钉孔和立柱对齐，向左滑动。
       b.拧紧两颗螺钉，将转接卡固定在 PCIe 支架上。
       
      ![image](https://user-images.githubusercontent.com/117898035/202676618-39c59543-1694-48e4-8859-ea94b6eb98a5.png)
      
    - 步骤 2. 将线缆连接到转接卡上。
    - 步骤 3. 安装 PCIe 适配器：解锁 PCIe 支架上的螺丝，旋转打开 latch ,将 PCIe 适配器对齐转接卡上的插槽，然后轻轻地按压 PCIe 适配器的两端，直到适配器在插槽上牢固就位,最后旋回 latch，紧锁螺丝固定。
   
      ![image](https://user-images.githubusercontent.com/117898035/202676656-474e611a-ebef-4399-92e9-8de9b56ba2c4.png)
   
    - 步骤 4. 安装 PCIe 模组。
       a.将装有 PCIe 适配器的支架上的销钉和孔与机箱上的孔和销钉对齐，并向下放置。
       b.锁紧一颗螺钉固定 PCIe 模组。
       
       ![image](https://user-images.githubusercontent.com/117898035/202676699-de3cee41-696a-4969-865f-64bbb81dfc0f.png)

- **安装后置 PCIe 模组**

  **步骤**
   - 步骤 1. 组装 PCIe 模组。
       a.将转接卡螺钉孔和葫芦孔与 PCIe 支架上的螺钉孔和立柱对齐，向左滑动。
       b.拧紧两颗螺钉，将转接卡固定在 PCIe 支架上后，将线缆连接到转接卡上。
      
      ![image](https://user-images.githubusercontent.com/117898035/202676754-73cb29b4-ccb5-4f65-a235-ffbacc441ebd.png)
      
      c.将 PCIe 适配器对齐转接卡上的插槽，然后轻轻地按压 PCIe 适配器的两端，直到适配器在插槽上牢固就位。
      
      ![image](https://user-images.githubusercontent.com/117898035/202676787-2633f23d-60a0-4d66-ba86-1af3a312680b.png)
      
      步骤 2. 安装系统风扇。
        a.将系统风扇插到 OCP 支架的风扇仓内。
        b.按压铆钉固定风扇。
	
        ![image](https://user-images.githubusercontent.com/117898035/202676869-7cae8e47-bab1-408f-bf11-2c583d2f1d8f.png)
        
      步骤 3. 将装有 PCIe 适配器的支架向下插入到 OCP 支架上，组成 PCIe 模组。
      
      ![image](https://user-images.githubusercontent.com/117898035/202676899-f9abc1eb-694e-478b-8eab-3e0be9259da1.png)

      步骤 4. 安装后置 PCIe 模组。
        a.把后置 PCIe 模组插入硬盘仓，并向机箱正面推动。
        b.锁紧一颗螺钉固定后置 PCIe 模组。
        
      ![image](https://user-images.githubusercontent.com/117898035/202676933-1019e76f-8c47-44ba-afe3-975854aec1b6.png)

#### 卸下导风罩

    ![image](https://user-images.githubusercontent.com/117898035/202690907-6f19342b-4bb3-429f-8d9b-1472bb0b8052.png)

  为充分散热，请不要在未安装主机上盖、导风罩、风扇的情况下运行服务器。如果服务器支持热插拔组件，请最大限度地减少打开主机上盖的时间。

   - 关闭服务器电源。
   - 将服务器从机架中取出。
   - 卸下主机上盖。
   - 卸下导风罩。
 
   ![image](https://user-images.githubusercontent.com/117898035/202677039-e91d4c02-0ec4-4954-9848-c4e04b2fd06c.png)
   
 （可选）如果服务器配置后置 IO,则服务器安装了后置导风罩。向上提起后置导风罩取出即可。
 
  ![image](https://user-images.githubusercontent.com/117898035/202677373-d24da1f0-8bfe-44f7-8135-4989a443dcf8.png)

#### 安装导风罩	

  ![image](https://user-images.githubusercontent.com/117898035/202677397-2ecbad38-3a1c-482d-b1b4-65f8367dc375.png)
  
  为避免损坏服务器组件，请勿用力安装导风罩。确保所有DIMM闩锁都已锁定，以免损坏组件。
  
  - 关闭服务器电源。
  - 将服务器从机架中取出。
  - 卸下主机上盖。
  - 安装导风罩。
  - 安装主机上盖。
  - 将服务器安装到机架中。
  - 接通服务器电源。
 
  ![image](https://user-images.githubusercontent.com/117898035/202677457-7ef8c3c9-805d-4f8b-828c-9cdd9b80ff6c.png)

  （可选）后置IO配置时，需要安装后置导风罩。将导风罩两侧的卡槽与机箱对齐，向下放入服务器并按压导风罩，直至其牢固就位。
  
  ![image](https://user-images.githubusercontent.com/117898035/202677483-47e64476-2700-4cc1-b952-25cba891e190.png)

#### 移除风扇模组

  ![image](https://user-images.githubusercontent.com/117898035/202677508-061171e3-dbfe-4f9e-9374-4cf871b7c164.png)
  
  操作时务必佩戴劳保手套，避免双手被设备上的尖锐部分划伤。
  
    -	确定需要拆卸的风扇模块。
    -	按压风扇模块一侧把手，将风扇模块水平拉出。
    
    ![image](https://user-images.githubusercontent.com/117898035/202677547-ba9a0e5f-9609-48eb-9faf-c878d00a1dc0.png)

#### 安装风扇模组	
  ![image](https://user-images.githubusercontent.com/117898035/202677571-a262ace6-8c0e-41cf-83b8-bc684c3f8a17.png)
  
  操作时务必佩戴劳保手套，避免双手被设备上的尖锐部分划伤。

   - 确定风扇模块的安装槽位。
   - 确定风扇的安装方向。
   - 沿水平方向将风扇模块插入机箱中，直到机箱扣紧风扇模块为止。
   - 重复2～3步骤安装其余的风扇模块。
  
   ![image](https://user-images.githubusercontent.com/117898035/202677631-cd6154ac-8f1c-4bce-9e20-eb5cd7821c90.png)

## **声明**

  感谢您选择京东云服务器产品。
  
  - 京东云可能不会在所有国家或地区都提供本文档中讨论的产品、服务或者功能特性。有关您当前所在区域的产品和服务的信息，请向您当地的京东代表咨询。
  - 京东云提供本手册，不附有任何种类的（无论是明示的还是默示的）保证，包括但不限于默示的有关非侵权、适销和适用于某特定用途的保证。某些管辖区域在特定交易中不允许免除明示或暗含的保证，因此本声明可能不适用您。
  - 本手册的用途在于帮助您正确地使用京东服务器产品（以下称“本产品”），在安装和第一次使用本产品前，请您务必先仔细阅读随机配送的所有数据，特别是本手册中所提及的注意事项。这会有助于您更好和安全地使用本产品。请妥善保管本手册，以便日后参阅。
  - 对本产品及相关服务的保证和保修承诺，应按可适用的协议或产品标准保修服务条款和条件操作。在法律法规的最大允许范围内，我们对于您的使用或不能使用本产品而发生的任何损害（包括但不限于直接或间接的个人损害、商业利润的损失、业务中断、商业信息的遗失或任何其它损失），不负任何赔偿责任。
  - 如您不正确地或未按本手册的指示和要求安装、使用或保管本产品，或让非京东授权的技术人员修理、变更本产品，京东将不对由此导致的损害承担任何责任。
  - 对于您在本产品之外使用本产品随机提供的软件，或在本产品上使用非随机软件或经京东认证推荐使用的专用软件之外的其它软件，我们对其可靠性不做任何保证。
  - 本手册中所提供照片、图形、图表和插图，仅用于解释和说明目的，可能与实际产品有些差别，另外，产品实际规格和配置可能会根据需要不时变更，因此与本手册内容有所不同。
  - 本手册的描述并不代表对本产品规格和软、硬件配置的任何说明。有关本产品的实际规格和配置，请查阅相关协议、装箱单、产品规格配置描述文件，或向产品的销售商咨询。
  - 我们已经对本手册进行了仔细的校勘和核对，但我们不能保证本手册完全没有任何错误和疏漏，可能包含技术方面不够准确的地方或印刷错误，为更好地提供服务，京东云可以随时对本手册中描述的产品之软件和硬件及本手册的内容随时进行改进和修改，恕不另行通知。如果您在使用过程中发现本产品的实际情况与本手册有不一致之处，或您想得到最新的信息或有任何问题和想法，欢迎拨打京东客户服务热线(400-6022-618)。
