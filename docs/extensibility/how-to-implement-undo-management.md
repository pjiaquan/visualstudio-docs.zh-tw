---
title: "How to: 實作復原管理 | Microsoft Docs"
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
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# How to: 實作復原管理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

用來進行復原管理的主要介面是<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>，這由環境所實作。  若要支援復原管理，實作不同的復原單位 \(也就是<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>，其中可包含多個個別的步驟。  
  
 實作復原管理的方式視您的編輯器是否支援多重檢視而異。  以下各節會詳細說明每一個實作的程序。  
  
## 在編輯器可支援單一檢視的情況下  
 在這個案例中，編輯器不支援多個檢視。  只有一個編輯器和一份文件，以及它們支援復原。  使用下列程序來實作復原管理。  
  
#### 若要支援單一檢視編輯器的 \[復原管理  
  
1.  呼叫`QueryInterface`的`IServiceProvider`介面上的視窗框架`IOleUndoManager`，若要存取復原管理員於文件檢視物件 \(`IID_IOLEUndoManager`\)。  
  
2.  當檢視已決定位置到視窗外框時，它會取得站台的指標，它可以用它來呼叫`QueryInterface`的`IServiceProvider`。  
  
## 在編輯器可支援多個檢視的情況下  
 如果您有文件和檢視的分離，則通常有一個復原文件本身相關聯的管理員。  所有的復原單位會放在文件的資料物件相關聯的一個復原管理員。  
  
 復原管理員，其中還有另一個則用於每個檢視中，檢視查詢而非文件資料的物件呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>來具現化復原管理員，指定的 CLSID\_OLEUndoManager 類別識別項。  OCUNDOID.h 檔案中定義的類別識別項。  
  
 當使用<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>來建立您自己的復原管理員執行個體，請使用下列步驟來連結到環境的復原管理員。  
  
#### 若要復原管理員與檔案相連的環境  
  
1.  呼叫`QueryInterface`所傳回的物件上<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>的`IID_IOleUndoManager`。  儲存滑鼠指標以<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>。  
  
2.  Call `QueryInterface` on `IOleUndoManager` for `IID_IOleCommandTarget`.  儲存滑鼠指標以<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
3.  轉送您<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>和<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>呼叫預存`IOleCommandTarget`下列 StandardCommandSet97 命令介面：  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  Call `QueryInterface` on `IOleUndoManager` for `IID_IVsChangeTrackingUndoManager`.  儲存滑鼠指標以<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>。  
  
     使用滑鼠指標以<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>，以及<xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A>方法。  
  
5.  Call `QueryInterface` on `IOleUndoManager` for `IID_IVsLinkCapableUndoManager`.  
  
6.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A>與您的文件，它也應該實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient>介面。  您的文件關閉時，呼叫`IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`。  
  
7.  您的文件關閉時，呼叫`QueryInterface`上為您復原管理員`IID_IVsLifetimeControlledObject`。  
  
8.  請呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>。  
  
9. 當文件進行變更，會呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>上的管理員`OleUndoUnit`類別。  <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>方法保留物件參考，因此通常您在放開右後<xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>。  
  
 `OleUndoManager`類別代表單一的復原堆疊的執行個體。  因此，為每個正在追蹤復原或取消復原的資料實體的一個復原管理員物件。  
  
> [!NOTE]
>  復原管理員物件會廣泛地使用文字編輯器，則沒有特定的支援，讓文字編輯器\] 的一般元件。  如果您想要支援多層級的復原或取消復原，您可以使用這個物件，若要執行這項操作。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [如何: 清除復原堆疊](../extensibility/how-to-clear-the-undo-stack.md)