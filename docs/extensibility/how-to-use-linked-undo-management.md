---
title: "如何: 使用連結的復原管理 | Microsoft Docs"
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
  - "編輯器 [Visual Studio SDK]，舊版的管理連結的復原"
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 使用連結的復原管理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

連結的復原可讓使用者同時復原多個檔案中相同的編輯。  比方說，同時的文字會變更到多個程式檔案，例如標頭檔和 Visual c \+ \+ 檔案，是一個連結的復原交易。  連結的復原功能內建的復原管理員\] 中，環境的實作和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager>可讓您管理這項功能。  連結的復原的實作方法可以將連結在一起，被視為單一復原單位的不同復原堆疊的父系復原單位。  使用連結的復原的程序將有詳細說明下一節。  
  
### 若要使用連結的復原  
  
1.  Call `QueryService` on `SVsLinkedUndoManager` to get a pointer to `IVsLinkedUndoTransactionManager`.  
  
2.  建立初始的父連結的復原單位藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>。  這會設定為一群組成連結的復原堆疊的復原堆疊的起點。  在`OpenLinkedUndo`也必須指定您是否使用嚴格的或非絕對連結的復原的方法。  非絕對連結的復原行為表示某些連結的復原同層項目與文件可以關閉，並仍保留其他連結復原其堆疊上的同層級。  嚴格連結的復原行為指定所有連結的復原同層級堆疊必須一起復原或完全不復原。  加入後續的連結復原堆疊藉由呼叫 [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) 方法。  
  
3.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A>復原備份所有做為其中一個連結的復原單位。  
  
    > [!NOTE]
    >  若要實作連結的復原管理，在編輯器中，新增復原管理。  如需有關如何實作連結的復原管理的詳細資訊，請參閱 [How to： 實作復原管理](../extensibility/how-to-implement-undo-management.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [How to: 實作復原管理](../extensibility/how-to-implement-undo-management.md)