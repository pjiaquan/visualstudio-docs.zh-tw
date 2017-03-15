---
title: "設定基數命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.setradix"
helpviewer_keywords: 
  - "Debug.SetRadix 命令"
  - "設定基數命令"
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 設定基數命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

設定或傳回用來顯示整數值的數值基底。  
  
## 語法  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## 引數  
 `10` 或 `16` 或 `hex` 或 `dec`  
 選擇項。  指示十進位 \(10 或 dec\) 或十六進位 \(16 或 hex\)。  如果省略引數，則傳回目前的基數值。  
  
## 範例  
 這個範例會設定環境以十六進位格式顯示整數值。  
  
```  
>Debug.SetRadix hex  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)