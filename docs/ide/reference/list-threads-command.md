---
title: "列出執行緒命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listthreads"
helpviewer_keywords: 
  - "Debug.ListThreads 命令"
  - "列出執行緒命令"
  - "ListThreads 命令"
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 列出執行緒命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

顯示目前的程式中執行緒清單。  
  
## 語法  
  
```  
Debug.ListThreads [index]  
```  
  
## 引數  
 `index`  
 選擇項。  依照其索引選取一個執行緒成為目前的執行緒。  
  
## 備註  
 當指定時，`index` 引數會將指示的執行緒標示為目前的執行緒。  清單中目前執行緒旁邊會顯示一個星號 \(\*\)。  
  
## 範例  
  
```  
>Debug.ListThreads   
```  
  
## 請參閱  
 [列出呼叫堆疊命令](../../ide/reference/list-call-stack-command.md)   
 [列出反組譯碼命令](../../ide/reference/list-disassembly-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)