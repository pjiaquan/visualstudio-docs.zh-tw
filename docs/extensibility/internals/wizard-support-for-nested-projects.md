---
title: "巢狀專案的精靈支援 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "新增項目精靈"
  - "巢狀的專案精靈支援"
  - "新專案精靈"
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 巢狀專案的精靈支援
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IDE 會執行兩個可實作巢狀專案的父專案的精靈: **新的專案** 精靈和 **加入項目**精靈。  
  
 如果使用者啟動**新的專案**精靈藉由選取**加入專案**，按一下 **新的專案**在 \[檔案\] 功能表上，或藉由選取**新增**上按滑鼠右鍵**新的專案**在方案總管\] 中，IDE 會執行**AddProject**命令與父專案的實作**AddProject**命令可能會傳回範本專案檔或有一組內容參數的精靈 \(.vsz\) 檔案。  
  
 同樣地，父專案的實作 **AddItem** 精靈傳回.vsz 檔具有一組不同的內容參數。  
  
 如需有關精靈的詳細資訊，請參閱[精靈 \(。Vsz\) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)， [內容參數](../../extensibility/internals/context-parameters.md)和[註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [巢狀專案](../../extensibility/internals/nesting-projects.md)