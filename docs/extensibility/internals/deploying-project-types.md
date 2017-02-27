---
title: "部署專案類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案 [Visual Studio SDK]，managed 程式碼"
  - "專案 [Visual Studio SDK]，彙總工具"
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 部署專案類型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 安裝新的專案類型彙總 \(ProjectAggregator2.dll\) 以及 Windows Installer 套件 \(ProjectAggregator2.msi\) 可轉散發。 您必須使用新的彙總工具適用於 managed 程式碼專案類型。 ProjectAggregator2 運作措施讓您限制 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案正常運作時，防止 managed 程式碼專案類型的彙總工具。 下列步驟說明如何變更要使用新的彙總工具 VSPackage。  
  
1.  從方案中移除 NativeHierarchyWrapper 專案。  
  
2.  從安裝程式移除任何 NativeHierarchyWrapper 二進位檔。  
  
3.  將 ProjectAggregator2.msi 加入您的設定。