---
title: "偵錯封裝 | Microsoft Docs"
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
  - "偵錯 [偵錯 SDK]，封裝"
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 偵錯封裝
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

偵錯封裝執行 Visual Studio 命令介面中，並且會處理所有的使用者介面。  它會使用偵錯介面的 Visual Studio，並與工作階段偵錯管理員 \(SDM\) 通訊。  
  
 中斷事件傳送到 SDM 切換與偵錯工具執行模式下中斷模式，並將焦點變更至中斷的發生位置的程式。  偵錯封裝會追蹤的堆疊框架和執行緒從傳送至該事件的資訊。  
  
 偵錯封裝並沒有語言或執行階段環境的相依性。  您不需要執行或偵錯封裝的修改。  
  
 偵錯封裝是由 vsdebug.dll 實作的。  
  
## 請參閱  
 [偵錯的工作階段管理員](../../extensibility/debugger/session-debug-manager.md)   
 [堆疊框架](../../extensibility/debugger/stack-frames.md)   
 [執行緒](../../extensibility/debugger/threads.md)   
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)