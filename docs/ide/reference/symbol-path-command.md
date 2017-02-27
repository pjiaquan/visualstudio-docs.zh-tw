---
title: "符號路徑命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.symbolpath"
helpviewer_keywords: 
  - "Debug.SymbolPath 命令"
  - "符號路徑命令"
  - "SymbolPath 命令"
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# 符號路徑命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

設定偵錯工具目錄清單，以搜尋符號。  
  
## 語法  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## 引數  
 `pathname`  
 選擇項。  以分號分隔偵錯工具路徑清單，搜尋符號。  
  
## 備註  
 如果沒有指定 `pathname`，此命令會列出目前的符號路徑。  
  
## 範例  
 此範例將兩個路徑加入至符號目錄清單。  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## 範例  
 此範例顯示以分號分隔的目前符號路徑清單。  
  
```  
Debug.SymbolPath  
```  
  
## 請參閱  
 [命令視窗](../../ide/reference/command-window.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)