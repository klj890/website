---
title: "在 KubeSphere 中部署 MongoDB"
keywords: 'KubeSphere, Kubernetes, 安装, MongoDB'
description: '如何从 KubeSphere 应用商店部署 MongoDB'
linkTitle: "在 KubeSphere 中部署 MongoDB"
weight: 14250
---

[MongoDB](https://www.mongodb.com/) 是一个通用的、基于文档的分布式数据库，为现代应用开发者和云时代而打造。

本教程演示如何从 KubeSphere 应用商店部署 MongoDB。

## 准备工作

- 请确保[已启用 OpenPitrix 系统](../../../pluggable-components/app-store/)。
- 您需要创建一个企业空间、一个项目和一个用户帐户 (`project-regular`) 供本教程操作使用。该帐户需要是平台普通用户，并邀请至项目中赋予 `operator` 角色作为项目操作员。本教程中，请以 `project-regular` 身份登录控制台，在企业空间 `demo-workspace` 中的 `demo-project` 项目中进行操作。有关更多信息，请参见[创建企业空间、项目、帐户和角色](../../../quick-start/create-workspace-and-project/)。

## 动手实验

### 步骤 1：从应用商店中部署 MongoDB

1. 在 `demo-project` 项目的**概览**页面，点击左上角的**应用商店**。

   ![应用商店](/images/docs/zh-cn/appstore/built-in-apps/mongodb-app/app-store.PNG)

2. 找到 MongoDB，点击**应用信息**页面上的**部署**。

   ![应用商店中的 Mongodb](/images/docs/zh-cn/appstore/built-in-apps/mongodb-app/mongodb-in-app-store.PNG)

   ![部署 Mongodb](/images/docs/zh-cn/appstore/built-in-apps/mongodb-app/deploy-mongodb.PNG)

3. 设置名称并选择应用版本。请确保将 MongoDB 部署在 `demo-project` 中，点击**下一步**。

   ![确认部署](/images/docs/zh-cn/appstore/built-in-apps/mongodb-app/confirm-deployment.PNG)

4. 在**应用配置**页面，为该应用指定持久化存储卷，并记录用户名和密码用于访问该应用。操作完成后，点击**部署**。

   ![设置应用配置](/images/docs/zh-cn/appstore/built-in-apps/mongodb-app/set-app-configuration.PNG)

   {{< notice note >}}

   要为 MongoDB 指定更多值，请打开右上角的拨动开关查看 YAML 格式的应用清单文件，编辑其配置。

   {{</ notice >}}

5. 稍等片刻待 MongoDB 启动并运行。

   ![Mongodb 运行中](/images/docs/zh-cn/appstore/built-in-apps/mongodb-app/mongodb-running.PNG)

### 步骤 2：访问 MongoDB 终端

1. 转到**服务**页面，点击 MongoDB 的服务名称。

   ![Mongodb 服务](/images/docs/zh-cn/appstore/built-in-apps/mongodb-app/mongodb-service.PNG)

2. 在**容器组**下，展开菜单查看容器详情，然后点击**终端**图标。

   ![Mongodb 终端](/images/docs/zh-cn/appstore/built-in-apps/mongodb-app/mongodb-terminal.PNG)

3. 在弹出窗口中，直接向终端输入命令使用该应用。

   ![Mongodb 服务终端](/images/docs/zh-cn/appstore/built-in-apps/mongodb-app/mongodb-service-terminal.PNG)

   {{< notice note >}}

   如果您想从集群外部访问 MongoDB，请点击**更多操作**，选择**编辑外网服务**。在弹出的对话框中，选择 **NodePort** 作为访问方式。端口暴露后，使用该端口号访问 MongoDB。取决于您的 Kubernetes 集群的部署位置，您可能需要在安全组中放行端口并配置相关的端口转发规则。

   {{</ notice >}} 

4. 有关更多信息，请参见 [MongoDB 官方文档](https://docs.mongodb.com/manual/)。