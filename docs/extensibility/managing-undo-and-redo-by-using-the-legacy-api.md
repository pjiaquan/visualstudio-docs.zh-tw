---
title: "管理的復原和重複使用舊版 API | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊的復原管理"
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 管理的復原和重複使用舊版 API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

編輯器必須支援可讓使用者反轉最近的變更，它們就會修改程式碼時的復原作業。 大部分的編輯器下實作 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 可以自動提供整合式的開發環境 \(IDE\) 的復原支援。  
  
## 在本節中  
 [How to: 實作復原管理](../extensibility/how-to-implement-undo-management.md)  
 編輯器提供復原功能，與單一或多個檢視。  
  
 [如何: 清除復原堆疊](../extensibility/how-to-clear-the-undo-stack.md)  
 說明如何清除復原堆疊。  
  
 [如何: 使用連結的復原管理](../extensibility/how-to-use-linked-undo-management.md)  
 連結的復原管理納入您的編輯器。  
  
## 參考  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 提供復原管理支援多個檢視的編輯器。  
  
## 相關章節