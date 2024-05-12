## Cloud deployment models 

### Public Cloud

- 通过Internet access cloud
- 可向公众开放
- 多租户虚拟化，全球规模的基础设施
- 功能和定价不同

### Private Cloud

- 云仅由一个组织使用
- May reside in-house or off-premise
- 安全的专用基础设施，具有按需供应的好处，
- 不受网络带宽和可用性问题以及与公共云相关的安全威胁的负担。
- 具有更大的控制能力、安全性和弹性

### Hybrid Cloud

- 由多个云（public cloud, private cloud等）组成。它们仍然是独立的实体，但使用标准或专有协议进行互操作
- eg. 银行、医院、政府
- 允许应用程序和数据跨云流

## Cloud Computing Stack

![image-20240411175422805](assets\image-20240411175422805.png)

## Cloud Service Models

### Infrastructure-as-a-Service (IaaS) 

- 提供商提供作为服务提供的计算基础设施。
- 提供商管理大量的资源池，并使用虚拟化进行动态分配
- 客户“租用”这些物理资源，以定制他们自己的基础设施
- 完全控制操作系统、存储、应用程序和一些网络组件（如防火墙）

案例

Netflix从亚马逊网络服务（AWS）租用了数千台服务器、tb的存储空间。开发和部署专门的转码、存储、流媒体、分析等软件。除此之外，它还能够支持数千万计的连接设备，被来自40个+国家的4000万+用户使用



> laaS
>
> - 提供基础设施资源
> - IAAS适用于需要灵活和可扩展基础设施资源的场景，如开发和测试环境、高性能计算和灾备容灾。‘
> - 特点
>   - 灵活性和可拓展性，用户可以根据需求调整资源
>   - 资源集中管理
>     - 用户无需关注基础设置的维护，focus在业务开发上
>   - 付费模式灵活
>     - 按需付费，减少成本，可控
> - 应用
>   - 开发和测试
>   - 高性能计算
>   - 灾备和容灾解决方案

### Platform-as-a-Service (PaaS) 

- 提供商提供一个运行的软件平台或中间件
- 可以在平台之上开发、维护和部署自己的软件
- 运行该软件所需的硬件将由该平台进行自动进行管理。不能明确地要求使用资源
- 具有自动的可扩展性，无需响应请求负载的增加/减少，无需控制操作系统、存储或网络，但可以控制已部署的应用程序和主机环境

案例

最适合web应用程序，语言和API支持： Python、Java、PHP和Go



> PaaS
>
> - 提供开发和运行平台
> - PAAS适用于简化开发过程、快速部署和扩展的场景，如Web应用开发和移动应用开发。’
> - 特点
>   - 简化开发过程，提供了开发所需的基础平台
>   - 快速部署和拓展
>   - 多租户架构，多个用户共享相同的平台环境，提高资源利用率，但是用户相互隔离，保证安全性和稳定性
> - 应用
>   - web开发，移动开，大数据分析

### Software-as-a-Service (SaaS) 

供应商给你提供一个软件/应用程序。他们负责更新和维护它。‣你只需通过互联网使用该软件

案例

学校给学生和工作人员提供了Google Apps and Office 365 的使用服务



> SaaS
>
> - 提供软件应用程序
> - SAAS适用于降低部署和维护成本、快速获取软件功能的场景，如办公协作、客户关系管理和人力资源管理。
> - 特点
>   - 0部署和维护成本
>   - 灵活的订阅模式
>   - 快速升级和更新
> - 应用
>   - 办公协作和通信
>     - 文档编辑，邮件
>   - 客户关系管理软件和HR软件

 

### Other X-as-a-Service 

#### Function-as-a-Service (FaaS) 

- 用户以“云功能”的形式编写应用程序
- 用户定义触发这些函数执行的事件（例如，HTTP请求、网络钩子）
- 让云平台处理其他一切，包括资源供应、自动缩放、容错等。
- 用户只支付用于运行功能的CPU时间，用户不管理任何服务器，因此被称为“无服务器计算”

FaaS的好处

- 没有服务器管理，都由云提供商，不是用户低成本用户只支付CPU时间当功能执（免费当代码不运行）
- 灵活的缩放，不需要设置自动缩放：这是云提供商的问题
- 自动化高可用性和容错

案例

- AWS Lambda
- Google Cloud Functions

![image-20240411180411171](assets\image-20240411180411171.png)

![image-20240411180354782](assets\image-20240411180354782.png)



> Faas
>
> - 是什么
>   - FaaS（即功能即服务）是一种云计算服务，允许客户执行代码来响应事件，而无需管理通常与构建和启动微服务应用程序相关的复杂基础架构。
>   - 由于 FaaS 能够轻松隔离和扩展事务，因此它非常适合大容量和高度并行的工作负载。它还可用于创建后端系统或用于数据处理、格式转换、编码或数据聚合等活动。
> - 无服务器和功能即服务 (FaaS) 经常被混为一谈，但事实是 FaaS 实际上是无服务器的子集
> - 优缺点
>   - 优点
>     - 更多地关注代码，而不是基础架构：
>     - 使用资源时只需支付使用费：
>     - 自动扩展或缩减
>     - 获得强大的云基础架构的所有优势
> - 原则和最佳实践
>   - 让每个功能只执行一项操作
>   - 不要让功能调用其他功能（隔离



#### Machine-Learning-as-a-Service (MLaaS)

这是一组基于云的机器学习（ML）工具的总称，它涵盖了大多数ML管道，例如，数据预处理、模型训练、模型评估和预测，服务于MLaaS市场的四个关键参与者。亚马逊、微软Azure、谷歌云、IBM





> MLaas
>
> - 机器学习即服务
>   - 一种基于云平台的机器学习框架，为企业提供端到端的机器学习平台服务
> - 将机器学习集成的应用外包给第三方平台供应商，企业不再是自己完全独立从0到1搭建服务。‘
> - MLaaS平台还提供不同功能的API，这些API是已经经过训练的模型，对用户而言可以直接输入数据并从中获取结果。
> - 用例
>   - 自然语言处理(NLP)
>     数据探索
>     数据提取
>     结果预测
>     计算机视觉
>     语音识别
> - 优点
>   - 可扩展性
>     成本相对比较低
>     快速打通业务
>     使用更加便捷

## Issues of Cloud 

- 可用性：随时开放的服务有时可以被取消。
- 数据丢失
- 供应商锁定
- 安全性
- 隐私

## Challenges

- 存储
- scale
- faults和failures
- networking
- Machine heterogeneity