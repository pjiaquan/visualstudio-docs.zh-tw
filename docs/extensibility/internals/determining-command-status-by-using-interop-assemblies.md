---
title: "使用 Interop 組件來判斷命令狀態 | Microsoft Docs"
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
  - "interop 組件，判斷命令狀態"
  - "命令處理使用 interop 組件狀態"
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 使用 Interop 組件來判斷命令狀態
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage 必須持續追蹤的命令，它可以處理的狀態。 在 VSPackage 中處理的命令會變成啟用或停用時，無法判斷環境。 它負責 VSPackage 通知有關命令狀態的環境，例如，一般狀態這類命令 **剪下**, ，**複製**, ，和 **貼上**。  
  
## 狀態通知來源  
 環境會接收到 VSPackages' 命令的相關資訊 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法，這是實作 VSPackage 的一部分的 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面。 環境呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackage 在兩個情況下的方法:  
  
-   當使用者開啟主功能表或內容功能表 \(以滑鼠右鍵按一下\) 時，環境執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 該功能表上的命令，以判斷其狀態的所有方法。  
  
-   當 VSPackage 要求環境更新目前的使用者介面 \(UI\)。 這是目前顯示給使用者，例如，命令就會發生 **剪下**, ，**複製**, ，和 **貼上** 分組在 \[標準\] 工具列上，成為啟用和停用在回應內容和使用者的動作。  
  
 殼層裝載多個 VSPackages，因為殼層的效能會造成這個現象會降低，如果它需要用來輪詢來判斷命令狀態的每個 VSPackage。 相反地，在變更的時間，變更其 UI 時 VSPackage 應主動通知環境。 如需有關更新通知的詳細資訊，請參閱 [更新使用者介面](../../extensibility/updating-the-user-interface.md)。  
  
## 狀態通知失敗  
 VSPackage 失敗通知命令狀態變更的環境可以將 UI 置於不一致的狀態。 請記住，任何功能表或內容功能表命令的可放入工具列上的使用者。 因此，更新 UI，只在功能表或內容功能表開啟時，才是不夠的。  
  
## 請參閱  
 [VSPackages 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [實作](../../extensibility/internals/command-implementation.md)