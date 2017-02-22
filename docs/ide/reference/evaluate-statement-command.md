---
title: "評估陳述式命令 | Microsoft Docs"
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
  - "debug.evaluatestatement"
helpviewer_keywords: 
  - "Debug.EvaluateStatement 命令"
  - "評估陳述式命令"
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 評估陳述式命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

評估和顯示給定的陳述式。  
  
## 語法  
  
```  
Debug.EvaluateStatement text   
```  
  
## 引數  
 `text`  
 必要項。  要評估的陳述式。  
  
## 備註  
 用來輸入 **EvaluateStatement** 命令的視窗決定等號 \(\=\) 解釋為比較運算子或指派運算子。  
  
 在 \[**命令**\] 視窗中，等號 \(\=\) 是解釋為比較運算子。  所以，例如，如果變數值 `a` 和 `b` 是不同的，則命令  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 會傳回 `false` 的值。  
  
 相反地，在 \[**即時運算**\] 視窗中，等號 \(\=\) 是解釋為指派運算子。  所以，例如，命令  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 會將變數 `a` 的值指派為變數 `b` 的值。  
  
## 範例  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## 請參閱  
 [列印命令](../../ide/reference/print-command.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)