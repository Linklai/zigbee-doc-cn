 ***Z-Stack 3.0 开发指南 (Z-Stack 3.0 Developer's Guide)*** 
 =========================================================

- [ ***Z-Stack 3.0 开发指南 (Z-Stack 3.0 Developer's Guide)*** ](#z-stack-30-%E5%BC%80%E5%8F%91%E6%8C%87%E5%8D%97-z-stack-30-developers-guide)
- [**1. 引言 (Introduction)**](#1-%E5%BC%95%E8%A8%80-introduction)
    - [**1.1 目的 (Purpose)**](#11-%E7%9B%AE%E7%9A%84-purpose)
    - [**1.2 范围 (Scope)**](#12-%E8%8C%83%E5%9B%B4-scope)
    - [**1.3 术语及其定义 (Definitions, Abbreviations and Acronyms)**](#13-%E6%9C%AF%E8%AF%AD%E5%8F%8A%E5%85%B6%E5%AE%9A%E4%B9%89-definitions-abbreviations-and-acronyms)
    - [**1.4 参考文档 (Reference Documents)**](#14-%E5%8F%82%E8%80%83%E6%96%87%E6%A1%A3-reference-documents)
- [**2. ZigBee**](#2-zigbee)
    - [**2.1 设备类型 (Device Types)**](#21-%E8%AE%BE%E5%A4%87%E7%B1%BB%E5%9E%8B-device-types)
        - [**2.1.1 协调器 (Coordinator)**](#211-%E5%8D%8F%E8%B0%83%E5%99%A8-coordinator)
        - [**2.1.2 路由器 (Router)**](#212-%E8%B7%AF%E7%94%B1%E5%99%A8-router)
        - [**2.1.3 终端设备 (End-device)**](#213-%E7%BB%88%E7%AB%AF%E8%AE%BE%E5%A4%87-end-device)
    - [**2.2 栈配置文件 (Stack Profile)**](#22-%E6%A0%88%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6-stack-profile)
- [**3. 地址 (Addressing)**](#3-%E5%9C%B0%E5%9D%80-addressing)
    - [**3.1 地址类型 (Address types)**](#31-%E5%9C%B0%E5%9D%80%E7%B1%BB%E5%9E%8B-address-types)
    - [**3.2 网络地址分配 (Network address assignment)**](#32-%E7%BD%91%E7%BB%9C%E5%9C%B0%E5%9D%80%E5%88%86%E9%85%8D-network-address-assignment)
        - [**3.2.1 随机编址 (Stochastic Addressing)**](#321-%E9%9A%8F%E6%9C%BA%E7%BC%96%E5%9D%80-stochastic-addressing)
    - [**3.3 Z-Stack寻址 (Addressing in Z-Stack)**](#33-z-stack%E5%AF%BB%E5%9D%80-addressing-in-z-stack)
        - [**3.3.1 单点寻址/单播 (Unicast)**](#331-%E5%8D%95%E7%82%B9%E5%AF%BB%E5%9D%80%E5%8D%95%E6%92%AD-unicast)
        - [**3.3.2 间接寻址 (Indirect)**](#332-%E9%97%B4%E6%8E%A5%E5%AF%BB%E5%9D%80-indirect)
        - [**3.3.3 广播寻址/广播 (Broadcast)**](#333-%E5%B9%BF%E6%92%AD%E5%AF%BB%E5%9D%80%E5%B9%BF%E6%92%AD-broadcast)
        - [**3.3.4 组寻址/组播 (Group Addressing)**](#334-%E7%BB%84%E5%AF%BB%E5%9D%80%E7%BB%84%E6%92%AD-group-addressing)
    - [**3.4 重要设备地址 (Important Device Addresses)**](#34-%E9%87%8D%E8%A6%81%E8%AE%BE%E5%A4%87%E5%9C%B0%E5%9D%80-important-device-addresses)
- [**4. 绑定 (Binding)**](#4-%E7%BB%91%E5%AE%9A-binding)
    - [**4.1 建立绑定表 (Building a Binding Table)**](#41-%E5%BB%BA%E7%AB%8B%E7%BB%91%E5%AE%9A%E8%A1%A8-building-a-binding-table)
        - [**4.1.1 ZigBee设备对象绑定请求 (ZigBee Device Object Bind Request)** ###](#411-zigbee%E8%AE%BE%E5%A4%87%E5%AF%B9%E8%B1%A1%E7%BB%91%E5%AE%9A%E8%AF%B7%E6%B1%82-zigbee-device-object-bind-request)
            - [**4.1.1.1 启动应用 (The Commissioning Application)**](#4111-%E5%90%AF%E5%8A%A8%E5%BA%94%E7%94%A8-the-commissioning-application)
            - [**4.1.1.2 ZigBee设备对象终端设备绑定请求 (ZigBee Device Object End Device Bind Request)**](#4112-zigbee%E8%AE%BE%E5%A4%87%E5%AF%B9%E8%B1%A1%E7%BB%88%E7%AB%AF%E8%AE%BE%E5%A4%87%E7%BB%91%E5%AE%9A%E8%AF%B7%E6%B1%82-zigbee-device-object-end-device-bind-request)
        - [**4.1.2 设备应用程序绑定管理器 (Device Application Binding Manager)**](#412-%E8%AE%BE%E5%A4%87%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F%E7%BB%91%E5%AE%9A%E7%AE%A1%E7%90%86%E5%99%A8-device-application-binding-manager)
        - [**4.1.3 查找和绑定 (Finding and binding)**](#413-%E6%9F%A5%E6%89%BE%E5%92%8C%E7%BB%91%E5%AE%9A-finding-and-binding)
    - [**4.2 配置源绑定 (Configuring Source Binding)**](#42-%E9%85%8D%E7%BD%AE%E6%BA%90%E7%BB%91%E5%AE%9A-configuring-source-binding)
- [**5. 路由 (Routing)**](#5-%E8%B7%AF%E7%94%B1-routing)
    - [**5.1 概述 (Overview)**](#51-%E6%A6%82%E8%BF%B0-overview)
    - [**5.2 路由协议 (Routing protocol)**](#52-%E8%B7%AF%E7%94%B1%E5%8D%8F%E8%AE%AE-routing-protocol)
        - [**5.2.1 路由发现和选择 (Route Discovery and Selection)**](#521-%E8%B7%AF%E7%94%B1%E5%8F%91%E7%8E%B0%E5%92%8C%E9%80%89%E6%8B%A9-route-discovery-and-selection)
        - [**5.2.2 路由维护 (Route maintenance)**](#522-%E8%B7%AF%E7%94%B1%E7%BB%B4%E6%8A%A4-route-maintenance)
        - [**5.2.3 路由过期 (Route expiry)**](#523-%E8%B7%AF%E7%94%B1%E8%BF%87%E6%9C%9F-route-expiry)
    - [**5.3 表存储 (Table storage)**](#53-%E8%A1%A8%E5%AD%98%E5%82%A8-table-storage)
        - [**5.3.1 路由表 (Routing table)**](#531-%E8%B7%AF%E7%94%B1%E8%A1%A8-routing-table)
        - [**5.3.2 路由发现表 (Route discovery table)**](#532-%E8%B7%AF%E7%94%B1%E5%8F%91%E7%8E%B0%E8%A1%A8-route-discovery-table)
    - [**5.4 多对一路由协议 (Many-to-One Routing Protocol)**](#54-%E5%A4%9A%E5%AF%B9%E4%B8%80%E8%B7%AF%E7%94%B1%E5%8D%8F%E8%AE%AE-many-to-one-routing-protocol)
        - [**5.4.1 多对一路由概述 (Many-to-One Routing Overview)**](#541-%E5%A4%9A%E5%AF%B9%E4%B8%80%E8%B7%AF%E7%94%B1%E6%A6%82%E8%BF%B0-many-to-one-routing-overview)
        - [**5.4.2 多对一路由发现 (Many-to-One Route Discovery)**](#542-%E5%A4%9A%E5%AF%B9%E4%B8%80%E8%B7%AF%E7%94%B1%E5%8F%91%E7%8E%B0-many-to-one-route-discovery)
        - [**5.4.3 路由记录命令 (Route Record Command)**](#543-%E8%B7%AF%E7%94%B1%E8%AE%B0%E5%BD%95%E5%91%BD%E4%BB%A4-route-record-command)
        - [**5.4.4 多对一路由维护 (Many-to-One Route Maintenance)**](#544-%E5%A4%9A%E5%AF%B9%E4%B8%80%E8%B7%AF%E7%94%B1%E7%BB%B4%E6%8A%A4-many-to-one-route-maintenance)
    - [**5.5 路由设置快速参考 (Routing Settings Quick Reference)**](#55-%E8%B7%AF%E7%94%B1%E8%AE%BE%E7%BD%AE%E5%BF%AB%E9%80%9F%E5%8F%82%E8%80%83-routing-settings-quick-reference)
    - [**5.6 路由器离网关联清理 (Router Off-Network Association Cleanup)**](#56-%E8%B7%AF%E7%94%B1%E5%99%A8%E7%A6%BB%E7%BD%91%E5%85%B3%E8%81%94%E6%B8%85%E7%90%86-router-off-network-association-cleanup)

# **1. 引言 (Introduction)** #

## **1.1 目的 (Purpose)** ##

本文将讲解德州仪器的 ZigBee 栈(Z-Stack)的一些组件及其功能，并阐述该栈中可配置的参数及其配置方法，让开发者清楚应该如何更改参数以适应应用程序的需求。

## **1.2 范围 (Scope)** ##

本文将介绍德州仪器的 *Z-Stack™* 发行版里的概念和设置。 Z-Stack 是一个兼容ZigBee标准和 ZigBee PRO 栈配置文件的 ZigBee-2015 栈。本文还介绍了 Z3.0 的附加功能以及这些功能如何兼容 Z3.0 或传统设备的方法。

## **1.3 术语及其定义 (Definitions, Abbreviations and Acronyms)** ##

 | 术语          | 解析                                              |
 | :------------ | :------------------------------------------------ |
 | AF            | 应用程序框架                                      |
 | AES           | 高级加密标准                                      |
 | AIB           | 应用支持子层信息库                                |
 | API           | 应用程序接口                                      |
 | APS           | 应用支持子层                                      |
 | APSDE         | 应用支持子层数据实体                              |
 | APSME         | 应用支持子层管理实体                              |
 | ASDU          | 应用支持子层服务数据报单元                        |
 | BDB           | 基本设备行为                                      |
 | BSP           | 板级支持包—— HAL&OSAL 通常认为是一个 BSP        |
 | CCM*          | 增强型 CBC-MAC 模式运算器                         |
 | EPID          | 扩展的个域网标识符                                |
 | GP            | 绿色能源                                          |
 | GPD           | 绿色能源设备                                      |
 | HAL           | 硬件抽象层                                        |
 | MSG           | 消息                                              |
 | MT            | Z-Stack 协议栈的监测和测试层                      |
 | NHLE          | 下一个更高层的实体                                |
 | NIB           | 网络基本信息                                      |
 | NWK           | 网络                                              |
 | OSAL          | Z-Stack 协议栈的操作系统抽象层                    |
 | OTA           | 空中下载                                          |
 | PAN           | 个域网                                            |
 | RSSI          | 接收信号强度指示                                  |
 | SE            | 智能能源                                          |
 | Sub-Device    | Zigbee 设备应用端点中的独立设备功能               |
 | TC            | 信任中心                                          |
 | TCLK          | 信任中心链接密钥                                  |
 | ZCL           | ZigBee 群集库                                     |
 | ZDO           | ZigBee 设备对象                                   |
 | ZHA           | ZigBee 家居自动化                                 |
 | ZC            | ZigBee 协调器                                     |
 | ZR            | ZigBee 路由                                       |
 | ZED           | ZigBee 终端                                       |

## **1.4 参考文档 (Reference Documents)** ##

1. Texas Instruments document SWRA195, Z-Stack API
2. Texas Instruments document SWRA194, Z-Stack OSAL API
3. Texas Instruments document SWRU354, Z-Stack 3.0 Sample Application User’s Guide.
4. Texas Instruments document SWRA353, Z-Stack OTA Upgrade User’s Guide.
5. ZigBee document 05-3474-21 ZigBee ZigBee Specification
6. ZigBee document 07-5123-06 ZigBee Cluster Library Specificiation
7. ZigBee document 13-0402-13 ZigBee Base Device Behavior
8. ZigBee document 14-0563-16 ZigBee Green Power specification

# **2. ZigBee** #

ZigBee 网络是一种由一些使用电池供电的设备连结成的多跳网络，这意味着两个设备在 ZigBee 网络中交换数据可能需要依赖其他的中间设备才能完成。ZigBee 网络的这种合作性质，要求网络中的设备都应

1. 具有执行特定网络的功能。
2. 可以配置某些参数为特定值。

设备所执行的网络功能决定其在网络中的角色，这称为设备类型。需要配置成特定值的一些参数以及这些参数的值被称为栈配置文件。

## **2.1 设备类型 (Device Types)** ##

ZigBee 网络中有三种逻辑设备类型：

1. 协调器 (Coordinator)
2. 路由器 (Router)
3. 终端设备 (End-device)

ZigBee 网络由一个具有组网能力的设备(协调器或路由器)、多个路由器和终端设备组成。  

Note：  
设备类型不会限制在特定设备上运行的应用程序的类型。

![Figure 1](https://raw.githubusercontent.com/Shanyaoxing12/zigbee-doc-cn/master/pic/0000.png)

Figure 1 是一个简单的 ZigBee 网络示意图，其中黑色的设备为协调器，红色的设备为路由器，白色的设备为终端设备。

### **2.1.1 协调器 (Coordinator)** ###

协调器是具有组网能力的设备，但它没有加入网络的能力，这意味着它只能创建自己的网络，而不能加入现有的网络。在创建网络时，协调器会先扫描现有的射频环境(RF environment)并选择一个信道和一个网络标识符(PAN ID)，然后启动网络。在 Z3.0 中，协调器会创建一个集中式的安全网络，并且被授权为该网络的信任中心，这意味着协调器是该网络的安全管理者，并且是唯一能够分发密钥并允许其它设备加入其创建的网络的设备。  

协调器也可以(可选)用来协助绑定网络中的应用程序级。  

协调器的主要任务是启动网络和管理密钥，除此之外，它的行为与路由器相似。需要注意的是，其它设备的入网和退网过程都必须有协调器的参与，因此协调器不能离开自己创建的网络。  

想进一步了解安全相关的内容，请参阅 第 10 章。

### **2.1.2 路由器 (Router)** ###

路由器具有以下能力：

1. 允许其它设备加入网络；
2. 多跳路由；
3. 协助其子设备通信。

在 Z3.0 中，路由器被授予组网能力，允许其创建分布式的安全网络。这种组网能力允许路由器创建没有安全管理者的网络，这意味着路由器一旦创建网络后，其在该网络中就没有任何特殊的作用。  

更多详细内容，请参阅 第 10 章。  

一般来说，路由器被要求是随时活跃的，因此路由器应该使用电源供电。

### **2.1.3 终端设备 (End-device)** ###

终端设备没有任何具体的维护和建设网络的责任，因此它可以选择进入休眠或是唤醒状态，并且通常可以使用电池对其进行供电。  

一般而言，终端设备对内存的要求较低。  


Notes：  
在 Z-Stack 中，设备类型通常在编译的时候通过编译选项(ZDO_COORDINATOR and
RTR_NWK)确定。所有的应用示例都提供了单独的项目文件以构建不同的设备类型。

## **2.2 栈配置文件 (Stack Profile)** ##

需要配置为特定值的栈参数集以及上述设备类型值被称为栈配置文件，这些参数和值由 ZigBee 联盟定义。  

在网络中的所有设备的栈配置文件都必须一致(即网络中的所有设备都必须具有栈配置文件且参数和值必须相同)。  

应用开发者可以将设备的栈配置文件设置成其它的值(非 ZigBee 标准的值)，但这样做的话，这个设备将不能与那些遵循 ZigBee 标准的设备进行互操作。这些不遵循 ZigBee 标准的设备搭建的网络被称为封闭网络(closed networks)，其栈配置文件被称为特定网络(network-specific)栈配置文件。  

设备的栈配置文件标识符存在于该设备的发送信标中，这使设备能够在加入网络前就可以确定网络的栈配置文件。其中：

1. 特定网络的栈配置文件的 ID 为 0；
2. 传统 ZigBee 的栈配置文件的 ID 为 1；
3. ZigBee PRO 的栈配置文件(被用在 Z3.0)的 ID 为 2。

栈配置文件标识符可以通过 **nwk_globals.h** 文件下的 **STACK_PROFILE_ID** 参数进行配置。值为 3 的标识符是为绿色能源设备保留的，它出现在各自的框架中。

# **3. 地址 (Addressing)** #

## **3.1 地址类型 (Address types)** ##

ZigBee 设备中有两种类型的地址：

* 64 位的 IEEE 地址(也称 MAC 地址或扩展地址)
* 16 位的网络地址(也称逻辑地址或短地址)

64 位地址是一种全球性的唯一的地址，一经分配便伴随设备的一生。它通常由制造商或被安装时设置，并且由 IEEE 组织进行维护和分配。  

有关如何获取这些地址块的更多信息，请访问 http://standards.ieee.org/regauth/oui/index.shtml.  

16 位地址在设备加入网络时被分配，并且被使用在网络中。它在网络中是唯一的，可以用于网络中的设备识别和发送数据。

## **3.2 网络地址分配 (Network address assignment)** ##

### **3.2.1 随机编址 (Stochastic Addressing)** ###

ZigBee PRO 使用随机(random)编址的方案来分配网络地址。该编址方案随机地将短地址分配给新的设备，并且该短地址确保与网络中的其它设备地址不重复。  

当一个设备加入时，它将获得其父设备随机生成的地址，随后向网络中的其它设备发出“设备声明(Device Announce)”(宣告包含该设备的短地址和扩展地址)。如果有其它设备具有相同的短地址，则网络中的设备(路由器)将向整个网络发出广播“网络状态——地址冲突(Network Status – Address Conflict)”，并且所有具有冲突地址的设备将更改其短地址。在冲突设备改变它们的地址后，它们会发出各自的“设备声明”检查它们的新地址是否在网络中发生冲突。  

终端设备不参与“地址冲突”，其父设备会为其处理这个事件。如果终端设备上发生“地址冲突”，其父设备会向其发送“重新加入响应(Rejoin Response)”，以更改其短地址。在更新地址后，终端设备会发出“设备声明”以检查其新地址在网络中是否在冲突。  

当收到“设备声明”时，关联表和绑定表将被更新为新的短地址，路由表信息不会被更新(必须建立新的路由)。如果父设备确定“设备声明”属于其子设备下的一个子设备，而不是其直接的子设备，则父设备会认为该子设备已经迁移到另一个父设备。

## **3.3 Z-Stack寻址 (Addressing in Z-Stack)** ##

通常使用 **AF_DataRequest()** 函数将数据发送给ZigBee网络上的设备。 **afAddrType_t** (在 **ZComDef.h** 文件中定义)为数据包发送的目标设备的类型。

    typedef struct
    {
        union
        {
            uint16      shortAddr;
            ZLongAddr_t extAddr;
        } addr;
        afAddrMode_t    addrMode;
        byte            endPoint;
    } afAddrType_t;

Note:  
除了网络地址外，还需要指定寻址模式。目标寻址模式可以选择一个以下的值(AF寻址模式在 **AF.h** 文件中定义)：

    typedef enum
    {
        afAddrNotPresent = AddrNotPresent,
        afAddr16Bit      = Addr16Bit,
        afAddr64Bit      = Addr64Bit,
        afAddrGroup      = AddrGroup,
        afAddrBroadcast  = AddrBroadcast
    } afAddrMode_t;

寻址模式是必要的，因为在 ZigBee 网络中，数据包可以通过单播(unicast)、组播(multicast)或广播(broadcast)的模式发送。单播模式下，数据包会被发送到一台设备上；组播模式下，数据包会被发送到设备组上；广播模式下，数据包通常被发送到网络中的所有设备上。

### **3.3.1 单点寻址/单播 (Unicast)** ###

这是一种常规的寻址模式，该模式下可以将数据包发送到已知网络地址的当个设备上。使用该模式发送数据包，需要将 **addrMode** 设置成 **Addr16Bit** ，并且将目标设备的网络地址加载到数据包中。  

### **3.3.2 间接寻址 (Indirect)** ###

当不知道数据包的最终目的地的时，可以使用该寻址模式，该模式不需要指定目标地址，因为它会从发送设备的栈中的“绑定表(binding table)”中查找目标。这也被称为源绑定(Source binding)，详细内容请参阅后文与绑定有关的内容。使用该模式发送数据包，需要将 **addrMode** 设置成 **AddrNotPresent** 。  

当数据包被发送到栈时，目标地址和端点将从绑定表中被查找和使用。如果在绑定表中找到多个目标设备，则会将数据包的副本发送给这些设备。如果找不到绑定条目，则数据包将不会被发送。

### **3.3.3 广播寻址/广播 (Broadcast)** ###

当需要向网络中的所有设备发送数据包时，可以使用该寻址模式。使用该模式发送数据包，需要将 **addrMode** 设置成 **AddrBroadcast** ，并且目标地址可以设置为以下的广播地址之一：

1. **NWK_BROADCAST_SHORTADDR_DEVALL** (0xFFFF) – 消息将被发送到网络中的所有设备(包括休眠设备)。对于休眠设备，消息保留在其父设备，直到休眠设备轮询或消息超时( **f8wConfig.cfg** 文件中的 **NWK_INDIRECT_MSG_TIMEOUT** )
2. **NWK_BROADCAST_SHORTADDR_DEVRXON** (0xFFFD) – 消息将被发送到空闲时接收器打开的所有设备( **RXONWHENIDLE** )，即除了休眠设备外的所有设备
3. **NWK_BROADCAST_SHORTADDR_DEVZCZR** (0xFFFC) – 将消息发送给所有路由器(包括协调器)

### **3.3.4 组寻址/组播 (Group Addressing)** ###

当希望将数据包发送给一组设备时，可以使用该寻址模式。使用该模式发送数据包，需要将 **afAddrGroup** 和 **addr.shortAddr** 设置成组标识符。在使用该模式前，必须在网络中定义组(参阅 Z-Stack API[1] 文档中的 **aps_AddGroup()** )。  

Note：  
组寻址可以与间接寻址结合使用，在绑定表中的目标地址可以是单播地址或组播地址。另外，广播寻址只是提前设置好群组的一种组寻址的特例。  

将设备添加到标识符为 1 的组中，示例代码：

    aps_Group_t group;

    // Assign yourself to group 1
    group.ID = 0x0001;
    group.name[0] = 6; // First byte is string length
    osal_memcpy( &(group.name[1]), “Group1”, 6);
    aps_AddGroup( SAMPLEAPP_ENDPOINT, &group );

## **3.4 重要设备地址 (Important Device Addresses)** ##

应用程序可能需要知道自身的地址和父设备的地址。  

使用下列函数可以获取本设备的地址(在 Z-Stack API[1] 文档中定义)：

* **NLME_GetShortAddr()** – 返回本设备的 16 位网络地址
* **NLME_GetExtAddr()** – 返回本设备的 64 位扩展地址

使用下列函数可以获取父设备的地址(在 Z-Stack API[1] 文档中定义，这些函数中的术语“Coord”不是指协调器，而是指设备的父设备)：

* **NLME_GetCoordShortAddr()** – 返回父设备的 16 位网络地址
* **NLME_GetCoordExtAddr()** – 返回父设备的 64 位扩展地址

# **4. 绑定 (Binding)** #

绑定是一种应用程序之间(两个或多个)消息流的控制机制。在所有设备中实施的绑定机制，称为源绑定。  

绑定允许应用程序在不知道目标地址的情况下发送数据包，APS 层会从其绑定表中确定目标地址，然后将消息转发到应用目标(或多个应用目标)或应用组上。

## **4.1 建立绑定表 (Building a Binding Table)** ##

有 4 种方法建立绑定表：

1. ZigBee 设备对象绑定请求(ZigBee Device Object Bind Request) – 启动工具可以告诉设备制作一个绑定记录
2. ZigBee 设备对象终端设备绑定请求(ZigBee Device Object End Device Bind Request) – 两个设备可以把它们想要设置的绑定表记录告诉协调器，协调器将对它们进行匹配并创建绑定表条目
3. 设备应用程序(Device Application) – 设备上的应用程序可以建立或管理绑定表
4. 在发起设备的启动过程中查找和绑定(Finding and Binding commissioning process for initiator devices)

### **4.1.1 ZigBee设备对象绑定请求 (ZigBee Device Object Bind Request)** ### 

任何设备或应用都可以向其它设备(over the air)发送 ZDO 消息，以便为网络中的其它设备创建绑定记录，这称为协助绑定，发送消息的设备将创建绑定条目。

#### **4.1.1.1 启动应用 (The Commissioning Application)** ####

应用程序可以通过调用 **ZDP_BindReq()** [在 **ZDProfile.h** 中定义]并在绑定记录中包含 2 个 applications (地址和端点)来完成这个操作。第一个参数(target **dstAddr** )为绑定源地址的短地址(绑定记录将存储在该地址中)。调用 **ZDP_UnbindReq()** 并传入参数可以删除绑定记录。  

目标设备会返回ZigBee设备对象绑定(ZigBee Device Object Bind)或解绑(Unbind Response)的响应信息，协调器上的 ZDO 代码会通过调用 **ZDApp_ProcessMsgCBs()** 将返回的操作状态解析并通知 **ZDApp.c** 。  

响应绑定时，协调器返回的状态将会是 **ZDP_SUCCESS** 、 **ZDP_TABLE_FULL** 、 **ZDP_INVALID_EP** 或 **ZDP_NOT_SUPPORTED** 。  

响应解绑时，协调器返回的状态将会是 **ZDP_SUCCESS** 、 **ZDP_NO_ENTRY** 、 **ZDP_INVALID_EP** 或**ZDP_NOT_SUPPORTED** 。

#### **4.1.1.2 ZigBee设备对象终端设备绑定请求 (ZigBee Device Object End Device Bind Request)** ####

该机制是在超时时间内，通过对选定的设备使用按钮按压或其它类似的动作来进行绑定。协调器在超时时间内收集终端设备的绑定请求消息，并根据配置文件 ID (profile ID )和 簇 ID (cluster ID)的协定生成绑定表条目。默认的终端绑定超时时间( **APS_DEFAULT_MAXBINDING_TIME** )为 16 秒 ( **nwk_globals.h** 中定义)，如果将其添加到 **f8wConfig.cfg** 中或作为编译标志，则可以对其进行更改。  

在终端设备的绑定过程中，协调器会注册 **ZD_RegisterForZDOMsg()** 以接收终端设备绑定请求， **ZDApp_RegisterCBs()** 中的绑定和解绑 ZDO 消息在 **ZDApp.c** 上定义。当收到这些消息时，这些消息会被发送到 **ZDApp_ProcessMsgCBs()** 中进行解析和处理。  

终端设备绑定是一个切换过程(toggle process)，这意味着在你初次执行这个过程时，它就会在请求设备中创建一个绑定条目，当你再次执行这个过程，它就会删除请求设备中的绑定。这就是为什么在后面的示例中，它会发送解绑请求，然后等待解绑结果，如果成功，则本来已存在绑定条目，否则它会发送绑定请求以创建条目。  

当协调器接收到 2 个匹配的终端设备的绑定请求时，它将启动在请求设备中创建源绑定条目的流程。如果在 ZDO 终端设备中发现匹配请求，协调器会执行以下步骤：

1. 向第一个设备发送 ZDO 解绑请求。终端设备绑定是切换过程，因此首先发送解除绑定以删除现有的绑定条目。
2. 等待 ZDO 解绑响应。如果响应状态为 **ZDP_NO_ENTRY** ，则发送 ZDO 绑定请求以在源设备中创建绑定条目；如果响应状态为 **ZDP_SUCCESS** ，则转到第一个设备的簇 ID (解除绑定删除条目 – 切换(the unbind removed the entry – toggle))。
3. 等待 ZDO 绑定响应。收到响应后，转到第一个设备的下一个簇 ID。
4. 第一个设备完成后，对第二个设备执行相同的过程。
5. 第二个设备完成后，将 ZDO 终端设备绑定响应消息发送给两个设备。

### **4.1.2 设备应用程序绑定管理器 (Device Application Binding Manager)** ###

在设备上输入绑定条目的另一种方法是让应用程序管理自己的绑定表，这意味着应用程序将通过调用以下绑定表管理函数对本地绑定表条目进行增删，参阅 Z-Stack API[1] 文档 - 绑定表管理章节：

* bindAddEntry() – 向绑定表中添加条目
* bindRemoveEntry() – 从绑定表中删除条目
* bindRemoveClusterIdFromList() – 从现有的绑定表中删除一个簇 ID
* bindAddClusterIdToList() – 添加一个簇 ID 到现有的绑定表中
* bindRemoveDev() – 通过地址引用删除所有条目
* bindRemoveSrcDev() – 通过源地址引用删除所有条目
* bindUpdateAddr () – 更新条目为另一个地址
* bindFindExisting () – 查找一个绑定表条目
* bindIsClusterIDinList() – 检查绑定表中现有的簇 ID
* bindNumBoundTo() – 具有相同地址的条目数(源或目标)
* bindNumOfEntries() – 表中的条目数量
* bindCapacity() – 允许最大的条目量
* BindWriteNV() – 在 NV 中更新表

### **4.1.3 查找和绑定 (Finding and binding)** ###

基础设备行为中定义了一种称为查找和绑定的启动方法，其过程依赖于识别簇和 ZDO 消息来允许启动设备查找具有匹配应用簇的设备。这种机制通常由用户触发，指定那些设备需要彼此“查找和绑定”，以便这些设备可以更高效地进行通信。更多详细，请参阅 15.7.2 节有关此方法的信息。  

## **4.2 配置源绑定 (Configuring Source Binding)** ##

要启用设备的源绑定，需要在 **f8wConfig.cfg** 中包含 **REFLECTOR** 编译标志和考虑 2 个绑定配置项( **NWK_MAX_BINDING_ENTRIES** & **MAX_BINDING_CLUSTER_IDS** )。 **NWK_MAX_BINDING_ENTRIES** 是绑定表中条目的最大数量， **MAX_BINDING_CLUSTER_IDS** 是每个绑定条目中簇 ID 的最大数量。绑定表保持在静态 RAM(未分配)中，因此每个条目的数量和条目的簇 ID 数量会影响 RAM 的使用量。每个绑定表条目的大小为 6 字节加上( **MAX_BINDING_CLUSTER_IDS** \* 2 个字节)。除了对 RAM 的使用量有影响外，绑定配置项还会影响地址管理器中的条目数。

# **5. 路由 (Routing)** #

## **5.1 概述 (Overview)** ##

网状网络被描述成这样的网络：通信的过程由各个分布式的对等路由协作完成。(A mesh network is described as a network in which the routing of messages is performed as a decentralized, cooperative process involving many peer devices routing on each others’ behalf.)  

路由对应用层是完全透明的，应用程序只需将需要发送的数据发送到栈中，栈会负责查找路径。这样，应用程序便不知道它事实上是在多跳网络中运行。  

路由还可以实现 ZigBee 网络的“自愈(self healing)”性质。即便一个无线链路断开了，路由功能也能找到一条避开已断开链路的新路径。这极大地提高了无线网络的可靠性，这是 ZigBee 的关键特性之一。  

多对一(Many-to-one)路由是一种特殊的路由方式，被用在处理涉及集中式流量的场景。该方式是 ZigBee PRO 功能集的一部分，可以极大程度地减少流量，特别是当网络中的所有设备都将数据包发送到网关或数据集中器时。详细描述请参阅 5.4 节。  

## **5.2 路由协议 (Routing protocol)** ##

ZigBee 使用基于 AODV(无线自组网按需平面距离向量路由协议(Ad-hoc On-demand Distance Vector))的专用路由协议。为了在传感网络中的使用简易，ZigBee 路由协议促进了环境的能力，可以有效地减少链路故障和数据包丢失，并且支持设备移动。  

邻居路由器是指彼此在同一无线网络中的路由器。每个路由器在“邻居表(neighbor table)”中跟踪其邻居，并在路由器收到来自邻居路由器的(单播，广播或信标)任何消息时更新“邻居表”。  

当路由器接收到其应用程序或其它设备的单播数据包时，NWK 层会按照以下过程转发数据包：

* 如果目标地址是路由器(包含其子设备)的邻居之一，则数据包将直接传送到目标设备上。否则路由器将检查其路由表，以查找一个与数据包目标地址相对应的路由条目。
* 如果有活动的目标地址对应的路由条目，数据包将被中继到存储在路由表条目中的下一跳地址。
* 如果单次传输尝试失败，NWK 层将重复传输数据包并等待确认传输过程的结果，最多重复 **NWK_MAX_DATA_RETRIES** (在 **f8wconfig.cfg** 中配置)次。
* 如果路由表中找不到活动的条目或最大重试次数后失败，则会启动路由发现，并且缓存数据包，直到该过程完成。

ZigBee终端设备不执行任何路由功能。希望向任何设备发送数据包的终端设备只需将数据包转发给其父设备，父设备会为其行使路由功能。同样地，当任何设备希望将数据包发送给终端设备并发起路由发现时，终端设备的父设备会代表其进行响应。  

Note：  
ZigBee 树状寻址(非 PRO)分配方案可以根据其地址派生出到任何目标地址的路径。在 Z-Stack中，若常规路由过程无法启动(通常由于缺少路由表空间)，则会使用此机制进行自动回退。  

在 Z-Stack 中，路由应用已被优化存储的路由表。通常地，每个目标设备都需要一个路由表条目。但是通过将特定父级的终端设备的所有条目和该父级设备的条目相合并，可以实现优化存储而不丢失任何功能。  

ZigBee 路由器(包括协调器)执行以下路由功能：

1. 路由发现和选择
2. 路由维护
3. 路由过期

### **5.2.1 路由发现和选择 (Route Discovery and Selection)** ###

路由发现是网络设备合作寻找和确立网络路径的过程。路由发现可以由任何路由器设备发起，并始终针对特定的目标设备执行。路由发现机制会搜索源设备和目标设备之间的所有可行的路由，并尝试选择最佳的路由。  

路由选择是选择出可行的最低开销的路径。每个设备和相邻设备的连接都有一个“连接开销(link costs)”，连接开销通常与接收信号强度相关。通过将路线上所有的连接开销相加，就可以得到整条路线的“路由开销(route cost)”。路由算法会尝试选择最低开销的路由。  

路由发现通过使用请求/响应包实现。源设备通过向其邻居广播请求(RREQ)包来请求目标地址的路由。当设备收到 RREQ 包时，它将转播 RREQ 包。在转播前，设备会将新的连接开销更新到 RREQ 包的开销字段中，并在其路由发现表(5.3.2)中添加条目。这样，RREQ 包就携带了它遍历的所有链路的开销成本总和。这个过程会一直重复，直到 RREQ 包到达目标设备。多个 RREQ 包将通过不同的路线到达目标设备，这些 RREQ 包中都包含了各个路线的开销成本。目标设备会选择最佳的 RREQ 包，并将路由响应(RREP)包发送回源设备。  

RREP 包会沿着原来的中间设备，返回到发出请求的源设备中。当 RREP 包返回到源设备时，中间设备更新其路由表以指示到目标设备的路由。每个中间设备中路由发现表被用来确定 RREP 包的下一跳返回源(即原 RREQ 的传播路径)，并将条目添加进路由表中。  

一旦创建了路由，就可以发送数据包。当一个设备丢失了它的一个下一跳连接(设备发送数据包时没有收到 MAC ACK)时，它会发送 RREP 包到所有可能接收到该包的设备上，并将丢失的连接标记成坏的(使其路由表失效)。在收到 RREQ、RREP 或 RERR 包后，设备将更新其路由表。

### **5.2.2 路由维护 (Route maintenance)** ###

网状网络提供路由维护和自愈能力。中间设备会沿着连接追踪链路上的失败传输。如果(相邻的)链路被确认为坏的，则上游设备将启动所有使用该链路的路由的路由修复。通过发起路由的再发现，直到下一次数据包到达该设备时，路由修复完成。如果路由的再发现无法启动，或因某种原因导致再发现失败，则设备会将路由错误(RERR)包发送回源设备，然后负责启动新的路由发现。无论如何，路线都会自动重新建立。

### **5.2.3 路由过期 (Route expiry)** ###

路由表维护那些已建立的路由条目。如果一段时间内没有数据包沿该路由发送，该路由将会被标记为过期。过期的路由不会被删除，除非存储空间不足。路由的自动过期时间可以在 **f8wconfig.cfg** 中配置。 **ROUTE_EXPIRY_TIME** 可以配置以秒为单位的过期时间，配置为 0 时会关闭路由过期的功能。

## **5.3 表存储 (Table storage)** ##

路由功能要求路由器维护一些表。

### **5.3.1 路由表 (Routing table)** ###

每个 ZigBee 路由器(包括协调器)都包含一个路由表，其存储了该设备参与的路由的必要信息。每个路由表条目都包含目标地址，下一跳设备和链路状态。所有发送到目标地址的数据包都会通过下一跳设备进行路由。此外，路由表中的条目可能会过期，以便回收表的空间。  

路由表容量指示设备路由表可存放的总条目数。路由表的大小可以通过 **f8wconfig.cfg** 中的 **MAX_RTG_ENTRIES** 进行配置(默认值为 40)。有关路由过期的详细信息，请参阅路由过期部分。

### **5.3.2 路由发现表 (Route discovery table)** ###

路由设备参与路由发现，并维护路由发现表。路由发现表用于路由发现进行时的临时信息存储。表中存储的条目只在其路由发现操作期间有效，一旦临时条目到期，它就可以被用于另一个路由发现操作。因此，路由发现表的最大条目值决定了可以在网络中同时执行的路由发现的最大数量。该值通过 **f8wconfig.cfg** 中的 **MAX_RREQ_ENTRIES** 进行配置。

## **5.4 多对一路由协议 (Many-to-One Routing Protocol)** ##

以下解释了多对一和源路由的过程，以便用户更好地理解 ZigBee 路由协议。事实上，所有的路由都在网络层进行处理，对应用程序来说是透明的。由应用程序决定发出多对一的路由发现和路由维护。

### **5.4.1 多对一路由概述 (Many-to-One Routing Overview)** ###

在 ZigBee PRO 中采用多对一路由可以帮助最大限度地减少流量，特别是在涉及集中式流量的场景时。低功耗无线网络通常具有充当网关或数据集中器的设备。网络中的所有设备至少应该维护一条到中心设备的有效路由，为了实现这一点，所有设备都必须依赖现有的(基于 ZigBee AODV的)路由解决方案，启动集中器的路由发现。路由的请求广播将会加在一起并在网络上产生巨大的影响。为了更好地优化路由解决方案，采用多对一路由以允许数据集中器利用单个路由发现来建立来自网络中所有设备的路由并且将路由发现广播风暴最小化。  

源路由时多对一路由的一部分，为集中器发送响应或确认信息回目标设备提供了一种有效的方式。集中器将从其到目标设备的完整路由信息放入需要传输的数据帧中。它最大限度地减少了网络中的路由表大小和路由发现流量。

### **5.4.2 多对一路由发现 (Many-to-One Route Discovery)** ###

下图显示了多对一路由的发现过程。为了发起多对一路由发现，集中器向整个网络广播多对一路由请求。一旦收到路由请求，每个设备都添加一个路由表条目到集中器并存储，将请求中继到下一跳地址的单跳邻居。该过程不会生成路由应答。

![Figure 2](https://raw.githubusercontent.com/Shanyaoxing12/zigbee-doc-cn/master/pic/0001.png)

多对一路由请求命令类似于具有相同命令 ID 和 负荷帧格式的单播路由请求命令。路由请求中的选择字段是多对一的，并且目标地址为 0xFFFC。以下 Z-Stack API 可以用于集中器发送多对一的路由请求(有关此 API 的详细用法，请参阅 Z-Stack API[1] 文档)：

    ZStatus_t NLME_RouteDiscoveryRequest( uint16 DstAddress, byte options, uint8 radius ) 

选择字段是一个位掩码，用于指定路由请求的选项，可以是以下的值：

 | 值   | 描述                                         |
 | :--- | :------------------------------------------- |
 | 0x00 | 单播路由发现                                 |
 | 0x01 | 路由缓存的多对一路由发现(集中器没有内存限制) |
 | 0x03 | 非路由缓存的多对一路由发现(集中器有内存限制) |

 当选项字段的值为 0x01 或 0x03 时， **DstAddress** 字段将被多对一的目标地址 0xFFFC 覆盖。因此，在多对一路由请求的情况下，用户可以将任何值传递给 **DstAddress** 。

### **5.4.3 路由记录命令 (Route Record Command)** ###

上述的多对一路由发现过程建立了从所有设备到集中器的路由。逆向路由(从集中器到其它设备)通过路由记录命令完成。源路由的过程如图 3 所示。R1 通过先前建立起的多对一路由向集中器发送数据包 DATA，并期望返回确认。为了提供路由给集中器发回 ACK，R1 会将路由记录命令随数据包一并发送，命令将记录数据包经过的路由，并向集中器提供一个逆向路由来发回 ACK。

![Figure 3](https://raw.githubusercontent.com/Shanyaoxing12/zigbee-doc-cn/master/pic/0002.png)

一旦接收到路由记录命令，中继路径上的设备会把它们自己的网络地址附加到路由记录命令的负荷帧的中继列表中。在路由记录命令达到集中器时，它将包含完整的路由路径(数据包中继到集中器所经过的路径)。当集中器将 ACK 发回 R1 时，它应该在数据包的网络层包头中包含源路由(中继列表)。所有接收数据包的设备都应该根据源路由将数据包中继到下一跳设备中。对于没有内存限制的集中器，它可以存储它收到的所有路由记录条目，并使用它们将数据包发送给源设备，所以设备只需要发送一次路由记录命令。但是，对于没有源路由缓存能力的集中器，设备总是需要将路由记录命令随数据包一并发送。集中器会将源路由临时存储在内存中，在使用后丢弃。  

简而言之，当网络中的大多数设备都将流量汇集到单个设备时，多对一路由可以有效地增强常规的 ZigBee 单播路由。作为多对一路由的一部分，源路由仅在某些情况下使用。首先，它在集中器响应源设备发起的请求时使用。其次，如果内存充足，集中器应该存储所有设备的源路由信息。否则，每当设备向集中器发出请求时，它们都需要发送路由记录。

### **5.4.4 多对一路由维护 (Many-to-One Route Maintenance)** ###

如果在设备转发多对一路由帧时遇到链路故障(请注意，多对一路由帧自身与常规单播数据包没有什么区别，但其路由表条目中有一个字段是用以指向集中器的)，设备将生成一个表示“多对一路由失败(Many-to-one route failure)”的代码的网络状态命令。网络状态命令将通过随机的邻居中继到集中器，并且希望该邻居仍有一个到集中器的有效路由。当集中器收到路由失败时，应用程序将决定是否重新发出多对一路由请求。  

当集中器收到指示多对一路由故障的网络状态命令时，它将指示传递给 ZDO 层，并调用 **ZDApp.c** 中的 ZDO 回调函数：

    void ZDO_ManytoOneFailureIndicationCB()

默认情况下，此函数会重启多对一路由发现以恢复路由。你可以修改这个函数，以适应更复杂的过程。

## **5.5 路由设置快速参考 (Routing Settings Quick Reference)** ##

 |                        |                                                             |
 | :--------------------- | :---------------------------------------------------------- |
 | 路由表大小(必须大于 4) | 配置 **MAX_RTG_ENTRIES** ，详情参见 5.3.1                   |
 | 路由过期时间           | 配置 **ROUTE_EXPIRY_TIME** ，详情参见 5.2.3                 |
 | 路由发现表大小         |　配置　**MAX_RREQ_ENTRIES** ，详情参见 5.3.2                |
 | 集中器使能             | 配置 **CONCENTRATOR_ENABLE** ，详情参见 **ZGlobals.h**      |
 | 集中器的路由缓存       | 配置 **CONCENTRATOR_ROUTE_CACHE** ，详情参见 **ZGlobals.h** |
 | 源路由表大小           | 配置 **MAX_RTG_SRC_ENTRIES** ，详情参见 **ZGlobals.h**      |
 | 集中器默认的广播半径   | 配置 **CONCENTRATOR_RADIUS** ，详情参见 **ZGlobals.h**      |

## **5.6 路由器离网关联清理 (Router Off-Network Association Cleanup)** ##

如果 ZigBee 路由器长时间离网，它的子设备将会尝试加入到另一个父设备下。当路由器重新入网时，其原本的子设备仍然会出现在其子设备表中，这样会阻碍出口流量正确地路由给子设备。  

为了避免这种情况，建议容易离网的并且在网络上的路由器将 **zgRouterOffAssocCleanup** 标记配置成 **TRUE** (映射到 NV 项：**ZCD_NV_ROUTER_OFF_ASSOC_CLEANUP** )

    uint8 cleanupChildTable = TRUE;
    zgSetItem( ZCD_NV_ROUTER_OFF_ASSOC_CLEANUP, sizeof(cleanupChildTable), &cleanupChildTable );

启用后，离网路由器的过期终端设备条目将从其子设备表中被移除(如果原子设备的流量已被其它父设备路由)。
