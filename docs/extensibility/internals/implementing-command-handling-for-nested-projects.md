---
title: "實作命令處理巢狀專案 | Microsoft Docs"
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
  - "巢狀的專案中，實作命令處理"
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 實作命令處理巢狀專案
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IDE 也能夠將命令傳遞到傳遞<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面，以巢狀的專案或父代專案可以篩選或覆寫的命令。  
  
> [!NOTE]
>  通常由父專案的命令可篩選資料。  例如命令**Build**和**Deploy** ，由 IDE 無法進行篩選。  
  
 下列步驟將說明實作命令處理的程序。  
  
## 程序  
  
#### 若要實作命令處理  
  
1.  當使用者選取巢狀的專案或節點巢狀專案中：  
  
    1.  IDE 呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。  
  
     \-或\-  
  
    1.  如果命令來自於階層架構\] 視窗中，例如快顯功能表指令，在 \[方案總管\] 中，IDE 便會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>在專案的父代的方法。  
  
2.  父專案可以檢查參數傳遞至`QueryStatus`，例如`pguidCmdGroup`和`prgCmds`，以判斷父專案是否應篩選命令。  如果父專案實作篩選命令後，它應該將它設定：  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     然後父專案應該會傳回`S_OK`。  
  
     如果父專案將不會篩選\] 指令，它應該只是傳回`S_OK`。  在此情況下，IDE 會自動在傳送命令至子專案。  
  
     若要將命令傳送至子專案沒有父專案。  IDE 會執行這項工作。.  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [命令、 功能表和工具列](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [巢狀專案](../../extensibility/internals/nesting-projects.md)