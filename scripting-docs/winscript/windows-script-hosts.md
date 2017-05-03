---
title: "Windows Script Host | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows Script Host, 實作主應用程式"
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Windows Script Host
當實作 Windows 架構的指令碼載入時，您可以安全地假設，一個指令碼引擎呼叫基礎執行緒中的 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 介面，只要主機執行下列動作:  
  
-   選取基礎執行緒 \(通常包含訊息迴圈的執行緒\)。  
  
-   具現化基礎執行緒的指令碼引擎。  
  
-   指令碼引擎只方法從基礎執行緒的呼叫，不過，明確地允許，在 [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) 和 [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md)的位置。  
  
-   呼叫指令碼引擎的分派只物件從基礎執行緒。  
  
-   如果提供，確保在基礎執行緒的訊息迴圈執行視窗控制代碼。  
  
-   確保只有主應用程式的物件模型做為事件來源的物件在基本的執行緒。  
  
 這些規則是由所有單一執行緒的主機自動追蹤。  所描述之受限制的模型頂端刻意很鬆散的可讓主應用程式藉由呼叫來自其他執行緒的 [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) 中止的就會的指令碼 \(啟始被同時處理常式或類似的\)，請使用 [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md)，、或迴圈在新執行緒上執行指令碼。  
  
## 備註  
 這些限制都不適用於選擇實作無限制執行緒的 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 介面的無限制執行緒物件模型的主機。  這類主應用程式可以從任何執行緒的 [IActiveScript](../winscript/reference/iactivescript.md) 介面，，不受限制。  
  
## 請參閱  
 [\<PAVE OVER\> Microsoft Windows 指令碼介面 \- 簡介](../Topic/%3CPAVE%20OVER%3E%20Microsoft%20Windows%20Script%20Interfaces%20-%20Introduction.md)