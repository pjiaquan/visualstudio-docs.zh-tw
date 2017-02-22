---
title: "Start 命令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.start"
helpviewer_keywords: 
  - "Debug.Start 命令"
  - "啟動命令"
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Start 命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

開始對啟動專案進行偵錯。  
  
## 語法  
  
```  
Debug.Start [address]  
```  
  
## 引數  
 `address`  
 選擇項。  程式暫停執行的位址，類似原始程式碼中的中斷點。  此引數只在偵錯模式中有效。  
  
## 備註  
 執行 **Start** 命令時，它會對指定的位址進行 RunToCursor 作業。  
  
## 範例  
 這個範例啟動偵錯工具，並且忽略發生的任何例外狀況。  
  
```  
>Debug.Start  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)