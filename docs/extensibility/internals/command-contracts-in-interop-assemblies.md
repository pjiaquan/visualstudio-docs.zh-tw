---
title: "Interop 組件中的命令合約 | Microsoft Docs"
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
  - "使用 interop 組件，命令合約處理的命令"
  - "interop 組件，命令合約"
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Interop 組件中的命令合約
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

處理命令的基本合約 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面是環境呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法來決定是否支援該命令，如果支援，以判斷其狀態和文字。 然後，環境會呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法執行命令。  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法相同的方式處理所有命令。 進一步的通訊，如有必要 \(例如，使用下拉式清單\) 由呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 方法搭配適當的參數。 這些參數的解譯取決於指定的命令。  
  
 命令目標的輸出參數中傳回值，如果呼叫端負責一律釋放已配置的任何資源。 這個參數是變數，因為清除變異釋放資源。  
  
 在其中命令必須在階層視窗中，運作的情況下 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 必須使用介面。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 介面都有類似的合約與類似的方法: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>。  
  
## 請參閱  
 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage 中的命令路由](../../extensibility/internals/command-routing-in-vspackages.md)   
 [實作](../../extensibility/internals/command-implementation.md)