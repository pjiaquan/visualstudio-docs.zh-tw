---
title: "篩選巢狀專案 AddItem 對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "篩選巢狀的專案"
  - "巢狀的專案，AddItem 對話方塊方塊篩選"
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 篩選巢狀專案 AddItem 對話方塊
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

當您顯示 **AddItem** 巢狀專案中，父專案\] 對話方塊中的可以控制哪些項目會顯示在對話方塊中。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>介面可讓您篩選將節點在 **AddItem** 對話方塊。  當子專案不會顯示 **AddItem** 對話方塊中，父代可實作`IVsFilterAddProjectItemDlg`介面和篩選器會顯示在子專案中的項目。  
  
 當專案會分組在特定的父專案的函式時，您可以實作`IVsFilterAddProjectItemDlg`使用者選取**加入專案項目**巢狀專案中的快顯功能表。  實作`IvsFilterAddProjectItemDlg displays`只有專案項目或檔案屬於該群組。  其他群組的專案項目是從篩選的對話方塊中，即使它們儲存在相同的目錄。  
  
 當使用者開啟 **AddItem** 對話方塊中，為子系的父專案的實作`IVsFilterAddProjectItemDlg`介面則稱為 「。  
  
 `IVsFilterAddProjectItemDlg`介面也可以實作類別來篩選。  如需詳細資訊，請參閱 [加入項目來加入新項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)和 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [加入項目來加入新項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [巢狀專案](../../extensibility/internals/nesting-projects.md)