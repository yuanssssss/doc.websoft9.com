---
sidebar_position: 1.0
slug: /production-deploy
---

# 生产级应用的部署要求

Websoft9 多应用托管平台，是一个面向生产的企业级的系统，即每个托管的应用都符合**生产级的部署方法**。

## 关于

在生产级部署中，仅仅让应用运行起来是远远不够的。   

它涉及到一系列更深入的考量，确保部署过程和运行效果都能达到企业级标准。以下是几个关键点：

1. **最大化基础设施性能**：确保应用充分利用可用的硬件和网络资源，以获得最佳性能。

2. **提高部署效率**：通过自动化和精细化的流程管理，减少部署过程中的错误，并缩短部署时间。

3. **持续优化与迭代**：部署后不断监控应用表现，并基于反馈进行优化，支持无缝的更新和再部署，以适应不断变化的需求和环境。

4. **安全性和可靠性**：确保所有的访问都是安全的，有防止数据泄露或未授权访问的措施，同时确保应用的高可用性和故障恢复能力。

通过这些综合措施，生产级部署能够保证应用不仅仅是在线，而且是高效、安全、可靠地服务于用户和业务需求。

## 准备云设施

使用 Websoft9 托管现代化的企业级云原生应用，需要一套完整、可靠且高效的基础设施作为支撑。

- [准备可用的域名](./domain-prepare)
- [规划整体基础设施](./design-infrastructure)
- [规划带宽和流量](./brandwith-infra)
- [扩充或优化存储](./storage)


## 准备安装包

准备安装包是部署工作至关重要的一步，不应被视作简单的前置任务。   

这一过程是独立而系统的，需要细致考虑安装包的格式、获取方式，以及实现安装包自动化编译的策略。

- [准备安装所需的软件包](./plan-package)
- [搜索 Websoft9 模板化应用](./appstore)

## 部署应用

在 Websoft9 托管平台上，用户针对任何类型的安装包都能享受到最高效的部署体验。

- [使用 Git 管理自动化部署](./plan-git)
- [使用 Websoft9 部署应用](./deployment)

## 发布应用

Websoft9 托管平台提供了一个专门的安全和访问控制模块，旨在保障应用的高可用性，确保应用发布的安全性和连续性。

- [设置应用的域名](./domain-set)
- [设置应用的 HTTPS 访问](./domain-https)
- [使用 CDN 实现全球加速](./gateway-cdn)

## 持续优化

Websoft9 托管平台提供了一整套完善的机制，支持应用的持续部署和持续优化过程。

- [设置 Docker 服务端](./docker-server)
- [应用自主配置与编排](./app-compose)
- [监控应用的运行情况](./monitor)
