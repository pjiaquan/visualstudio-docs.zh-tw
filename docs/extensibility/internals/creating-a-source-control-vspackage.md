---
title: "建立原始檔控制 VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "建立原始檔控制套件的原始檔控制 [Visual Studio SDK]，"
  - "原始檔控制套件"
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 建立原始檔控制 VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

這份文件包含連結至原始檔控制套件，與整合的架構概觀[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，由實作介面和服務的取用、 定義 API，並提供簡單的原始檔控制套件實作的範例。  
  
 原始檔控制 VSPackage，您可以建立與整合的原始檔控制的深度整合路徑[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  它可以讓封裝以略過預設的原始檔控制所裝載的 UI [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、 回原始檔控制要求專案系統中，並與其互動[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]元件，例如**方案總管\] 中**。  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]讓[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]夥伴可以和整合一套機制來建立 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用服務模型。  
  
## 在本節中  
 [使用者入門](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 將告訴您原始檔控制套件，也就是更進階的替代方案加入原始檔控制外掛程式的實作中的原始檔控制功能的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 [架構](../../extensibility/internals/source-control-vspackage-architecture.md)  
 顯示圖表，並說明 \[原始檔控制套件的元件。  
  
 [功能](../../extensibility/internals/source-control-vspackage-features.md)  
 說明各種功能的原始檔控制套件。  
  
 [設計元素](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 說明原始檔控制套件必須實作的深度整合的 VSPackage 結構。  
  
## 相關章節  
 [建立原始檔控制外掛程式](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 討論如何建立原始檔控制外掛程式，提供原始檔控制功能，在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]原始檔控制使用者介面 \(UI\)。  
  
 [原始檔控制](../../extensibility/internals/source-control.md)  
 討論的整合功能，以實作原始檔控制選項[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。