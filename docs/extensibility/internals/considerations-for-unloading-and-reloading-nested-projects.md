---
title: "卸載並重新載入巢狀專案的考量 | Microsoft Docs"
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
  - "巢狀的專案卸載及重新載入"
  - "專案 [Visual Studio SDK]，卸載及重新載入巢狀"
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 卸載並重新載入巢狀專案的考量
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

當您實作巢狀的專案類型時，您必須先執行額外的步驟，當您卸載並重新載入專案。  若要正確地通知方案事件的接聽程式，您必須正確地引發`OnBeforeUnloadProject`和`OnAfterLoadProject`事件。  
  
 您必須引發這些事件，以這種方式的其中一個原因是您不想原始程式碼控制 \(SCC\) 從伺服器刪除的項目，然後將它們新增為新的如果沒有`Get`從 SCC 的作業。  在此情況下，新的檔案會載入 SCC 之外，您必須卸載並重新載入所有的檔案，以備不同。  SCC 呼叫`ReloadItem`。  您的實作，該呼叫的是要刪除的專案，並重新建立它再實作`IVsFireSolutionEvents`呼叫`OnBeforeUnloadProject`和`OnAfterLoadProject`。  當您執行這項實作時，SCC 會通知關於專案已暫時刪除，並再次新增。  因此，SCC 不能進行專案時，如果專案實際從伺服器刪除，然後再次新增。  
  
## 重新載入專案  
 若要支援的巢狀專案重新載入，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A>方法。  在實作中的`ReloadItem`，您關閉巢狀的專案，然後再重新建立。  
  
 通常當重新載入專案，會在 IDE 引發<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A>和`M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)`事件。  不過，對於巢狀專案將會被刪除並重新載入，父專案啟動的處理程序中，而不是在 IDE。  因為父專案不會引發解決方案事件，IDE 會有任何程序的初始設定的相關資訊，都不會引發事件。  
  
 若要處理這個過程中，父專案的呼叫`QueryInterface`的<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents>介面關閉<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution>介面。  `IVsFireSolutionEvents`具有函式，判斷要引發 IDE `OnBeforeUnloadProject`卸載巢狀的專案，並接著引發的事件`OnAfterLoadProject`事件，以重新載入同一個專案。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [巢狀專案](../../extensibility/internals/nesting-projects.md)