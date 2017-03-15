---
title: "命令路由演算法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "命令路由"
  - "命令傳送"
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 命令路由演算法
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 Visual Studio 中許多不同的元件會處理命令。 命令會從最內部的內容中，根據目前的選取範圍，最外層 （也稱為全域） 的內容來路由傳送。 如需詳細資訊，請參閱[可用性](../../extensibility/internals/command-availability.md)。  
  
## 命令的解析順序  
 命令會先通過下列層級的命令內容︰  
  
1.  增益集︰ 環境先提供任何增益集所要的命令。  
  
2.  優先順序命令︰ 使用這些命令會註冊 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>。 它們會針對在 Visual Studio 中的每個命令呼叫，因此稱為 「 已註冊的順序。  
  
3.  內容功能表命令︰ 提供給內容功能表中，一般路由命令目標先提供\] 內容功能表上的命令。  
  
4.  工具列命令目標集︰ 當您呼叫註冊這些命令目標 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>。`pCmdTarget` 參數可以是 `null`。 如果不是 `null`, ，則此命令的目標用來更新您正在設定的工具列上的任何命令。 如果介面設定您的工具列，則它會傳遞做為視窗框架 `pCmdTarget` ，讓所有更新的命令視窗框架中，您工具列流經都甚至未取得焦點。  
  
5.  工具視窗︰ 工具視窗，通常會實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 介面中，也應該實作 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面，因此當工具視窗是作用中視窗時，Visual Studio 可以取得命令目標。 不過，如果工具視窗有焦點是 **專案** \] 視窗中，則此命令會路由傳送至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 介面就是選取的項目共同的父系。 如果此選項會跨越多個專案，此命令會路由傳送至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> 階層。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 介面包含 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> 上相對應的命令類似的方法 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面。  
  
6.  文件視窗中︰ 如果命令已在其.vsct 檔中設定 RouteToDocs 旗標，Visual Studio 會尋找文件檢視物件，可能是命令目標的執行個體 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 介面或文件物件的執行個體 \(通常 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 介面或 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 介面\)。 如果文件檢視物件不支援命令，Visual Studio 會路由至 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 傳回的介面。 （這是選擇性的文件資料物件的介面）。  
  
7.  目前的階層︰ 目前的階層可擁有使用中視窗或階層中選取專案 **方案總管\] 中**。 Visual Studio 會尋找 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 最新的或使用中，階層實作的介面。 階層應支援每當階層為作用中，即使文件視窗的專案項目有焦點時，都有效的命令。 不過，命令時，才套用 **方案總管\] 中** 具有焦點必須支援使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 介面及其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>方法。  
  
     **剪下**, ，**複製**, ，**貼上**, ，**刪除**, ，**重新命名**, ，**Enter**, ，和 **DoubleClick** 命令需要特殊處理。 如需有關如何處理資訊 **刪除** 和 **移除** 命令在階層中，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> 介面。  
  
8.  Global︰ 如果先前所述內容尚未處理命令，Visual Studio 會嘗試將它路由傳送至擁有實作命令的 VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面。 如果 VSPackage 尚未已經載入，它時不會載入 Visual Studio 會呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法。 只有當載入 VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法呼叫。  
  
## 請參閱  
 [命令設計](../../extensibility/internals/command-design.md)