---
title: "虚拟机网络管理"
date: 2019-07-19T17:38:36+08:00
weight: 10
description: >
  介绍虚拟机网络相关操作。
---

## Web界面操作

### 关联安全组

安全组是一种虚拟的包过滤防火墙，通过设置安全组规则来控制关联的虚拟机是否可以被访问，以及虚拟机可访问的外部资源等。在为虚拟机绑定安全组之前请先在网络-安全组页面创建安全组规则。批量关联安全组操作支持选择不同平台上的虚拟机。

**单个虚拟机关联安全组**

1. 在虚拟机页面，单击虚拟机右侧操作列 **_"更多"_** 按钮，选择下拉菜单 **_"网络安全-关联安全组"_** 菜单项，弹出关联安全组对话框。
2. 在关联安全组对话框中支持关联或取消关联安全组。
    - 关联安全组：选择要绑定的安全组，最多支持5个。如没有符合需求的安全组，可单击“新建安全组”超链接，在弹出的新建安全组页面配置相关参数，单击 “确定” 按钮，创建安全组。
    - 取消关联安全组：取消选择安全组，至少保留一个安全组。
3. 单击 **_"确定"_** 按钮，完成操作。

**批量关联安全组**

1. 在虚拟机列表中选择一个或多个虚拟机，单击 **_"批量操作"_** 按钮，选择下拉菜单 **_"网络安全-关联安全组"_** 菜单项，弹出关联安全组对话框。
2. 在关联安全组对话框中支持关联或取消关联安全组。
    - 关联安全组：选择要绑定的安全组，最多支持5个。如没有符合需求的安全组，可单击“新建安全组”超链接，在弹出的新建安全组页面配置相关参数，单击 “确定” 按钮，创建安全组。
    - 取消关联安全组：取消选择安全组，至少保留一个安全组。
3. 单击 **_"确定"_** 按钮，完成操作。

### 绑定弹性公网IP

弹性公网IP是一种NAT IP，通过与虚拟机绑定，实现虚拟机与公网之间的通信。

{{% alert title="注意" color="warning" %}}

- 目前ZStack、OpenStack平台的虚拟机在绑定弹性公网IP时不支持创建弹性公网IP，且不支持绑定属于同一IP子网的弹性公网IP；
- VMware平台的虚拟机不支持绑定弹性公网IP。
- 仅{{<oem_name>}}平台VPC网络的虚拟机支持绑定弹性公网IP。

{{% /alert %}}

1. 在虚拟机页面，单击虚拟机右侧操作列 **_"更多"_** 按钮，选择下拉菜单 **_"网络安全-绑定弹性公网IP"_** 菜单项，弹出绑定弹性公网IP对话框。
2. 配置以下参数
    - 若绑定方式选择“新建”弹性公网IP，
        - 当选择{{<oem_name>}}平台时配置以下参数：
            - 线路类型：可根据需求创建对应线路类型的EIP。
            - 网络计费方式：设置弹性公网IP的计费方式，包括按流量计费和按带宽计费。
                - 按流量计费：按实际传输流量收费，可限制峰值带宽避免意外流量带来的费用，当瞬间带宽超过该值时将丢包，适用于网络波动大的场合。
                - 按带宽计费：按传输速率计费，选择固定带宽，超过带宽时将丢包，适用于网络波动较小的场景。
            - 带宽：设置带宽大小。
        - 当选择公有云平台时配置以下参数：
            - 网络计费方式：设置弹性公网IP的计费方式，包括按流量计费和按带宽计费。
                - 按流量计费：按实际传输流量收费，可限制峰值带宽避免意外流量带来的费用，当瞬间带宽超过该值时将丢包，适用于网络波动大的场合。
                - 按带宽计费：按传输速率计费，选择固定带宽，超过带宽时将丢包，适用于网络波动较小的场景。
            - 带宽：设置带宽大小。
{{% alert title="注意" color="warning" %}}
        腾讯云和Azure不支持按固定带宽计费。
{{% /alert %}}
    - 若绑定方式选择“绑定已有”，请确保在弹性公网IP页面已存在对应平台的弹性公网IP，选择弹性公网IP。
3. 单击 **_"确定"_** 按钮。

### 解绑弹性公网IP
该功能用于解除虚拟机与弹性公网IP的绑定关系，释放弹性公网IP资源，释放后的弹性公网IP可以被其他虚拟机使用。

1. 在虚拟机页面，单击虚拟机右侧操作列 **_"更多"_** 按钮，选择下拉菜单 **_"网络安全-解绑弹性公网IP"_** 菜单项，弹出解绑弹性公网IP对话框。
2. 单击 **_"确定"_** 按钮，完成操作。

### 设置源/目标检查

源/目标检查即检查虚拟机接收或发送的流量的源/目标地址是否为虚拟机。启用检查时，当源/目标地址不是虚拟机时，则丢弃不处理；当虚拟机作为NAT、路由器、防火墙等使用时必须禁用源/目标检查。

仅{{<oem_name>}}平台的虚拟机支持设置源/目标检查且默认启用源/目标检查。

1. 在虚拟机页面，单击虚拟机右侧操作列 **_"更多"_** 按钮，选择下拉菜单 **_"网络安全-设置源/目标检查"_** 菜单项，弹出设置源/目标检查对话框。
2. 选择开启或关闭源/目标检查，单击 **_"确定"_** 按钮，完成操作。

### 补IP

当VMware虚拟机由于一些原因（如关机状态同步、未安装agent等）未同步到IP地址时，虚拟机列表的IP地址字段显示为"-"，此时支持为VMware虚拟机补IP。补充的IP地址必须与虚拟机的实际IP一致。

1. 在虚拟机列表中，当VMware平台虚拟机IP地址列为空时，单击IP地址列的 **_"可补IP"_** 按钮，弹出补充IP对话框。
2. 设置IP地址，单击 **_"确定"_** 按钮。

### 虚拟机网卡管理

该功能用于查看虚拟机的网卡信息，并支持针对网卡进行管理操作。

#### 添加网卡

该功能用于为虚拟机添加网卡，最多可添加8个网卡，目前仅{{<oem_name>}}平台的虚拟机支持添加网卡功能。

1. 在虚拟机页面，单击虚拟机名称项，进入虚拟机详情页面。
2. 单击“网络”页签，进入网络页面。
3. 单击网卡列表上方 **_"添加网卡"_** 按钮，弹出添加网卡对话框。
4. 设置VPC和IP子网，如需指定静态IP，可单击 **_"手动配置IP"_** 按钮，设置IP地址，单击 **_"确定"_** 按钮。

#### 修改带宽

该功能用于修改网卡的带宽限制。目前仅支持{{<oem_name>}}平台、VMware平台、ZStack平台、OpenStack平台。

1. 在虚拟机页面，单击虚拟机名称项，进入虚拟机详情页面。
2. 单击“网络”页签，进入网络页面。
3. 单击网卡右侧操作列 **_"修改带宽"_** 按钮，弹出修改带宽对话框。
4. 设置带宽，0表示无限制，取值范围为0~10000的整数。单击 **_"确定"_** 按钮。
5. 若开启了调整配置的工单，则还需要填入申请原因，单击 **_"提交工单"_** 按钮，提交修改带宽工单，等待审批通过后才会成功修改带宽。

#### 更换IP

该功能用于修改虚拟机的IP地址，支持在IP子网中动态分配IP地址或手动指定IP子网内的IP地址。目前仅支持{{<oem_name>}}平台、VMware平台。

1. 在虚拟机页面，单击虚拟机名称项，进入虚拟机详情页面。
2. 单击“网络”页签，进入网络页面。
3. 单击网卡右侧操作列 **_"更换IP"_** 按钮，弹出更换IP对话框。
4. 选择IP子网，如需指定静态IP，可单击 **_"手动配置IP"_** 按钮，设置IP地址，单击 **_"确定"_** 按钮。

#### 卸载网卡

该功能用于卸载虚拟机上的网卡，卸载时需要按照顺序卸载，只允许卸载最后一块网络，即序号最大的网卡支持卸载，所有网卡均可以被卸载。目前仅支持{{<oem_name>}}平台。

1. 在虚拟机页面，单击虚拟机名称项，进入虚拟机详情页面。
2. 单击“网络”页签，进入网络页面。
3. 单击最后一块网卡右侧操作列 **_"卸载"_** 按钮，弹出卸载网卡对话框。
4. 单击 **_"确定"_** 按钮，完成操作。
