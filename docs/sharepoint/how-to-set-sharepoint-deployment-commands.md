---
title: "如何：設定 SharePoint 部署命令 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visual Studio 中的 SharePoint 開發, 部署"
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 如何：設定 SharePoint 部署命令
  您可以設定預先部署和部署後命令來自訂部署程序。  當您從 Visual Studio 偵錯 SharePoint 方案時，這些命令會在其他部署動作之前和之後執行。  
  
### 若要加入預先部署命令  
  
1.  在功能表列上，選擇 \[**專案**\]、*ProjectName*\[**Properties**\]。  
  
2.  選擇 \[**SharePoint**\] 索引標籤。  
  
3.  在 \[**部署前命令列**\] 文字方塊中，輸入 MS\-DOS 或 MSBuild 命令以自訂此步驟。  
  
     例如，若要在部署完成前列出目錄內容，請輸入 **dir**。  
  
### 若要加入部署後命令  
  
1.  在功能表列上，選擇 \[**專案**\]、*ProjectName*\[**Properties**\]。  
  
2.  選擇 \[**SharePoint**\] 索引標籤。  
  
3.  在 \[**部署後命令列**\] 文字方塊中，輸入 MS\-DOS 或 MSBuild 命令以自訂此步驟。  
  
     例如，若要在部署完成後列出目錄內容，請輸入 **dir**。  若要使用 MSBuild 變數從組建目錄複製組件，請輸入 **copy $\(TargetPath\) c:\\DeploymentDirectory**。  
  
## 請參閱  
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  