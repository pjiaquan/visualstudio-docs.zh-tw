---
title: "切換中斷點命令 | Microsoft Docs"
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
  - "debug.togglebreakpoint"
helpviewer_keywords: 
  - "Debug.ToggleBreakPoint 命令"
  - "切換中斷點命令"
  - "ToggleBreakpoint 命令"
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 切換中斷點命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

根據中斷點目前的狀態，在檔案中的現行位置上，開啟或關閉中斷點。  
  
## 語法  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## 引數  
 `text`  
 選擇項。  如果指定 text，則該命令列標記為具名中斷點。  否則，該命令列標記為未命名的中斷點，類似按 F9 時所執行的動作。  
  
## 範例  
 下列範例切換目前的中斷點。  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)