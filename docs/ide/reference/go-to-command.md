---
title: "移至命令 | Microsoft Docs"
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
  - "edit.goto"
helpviewer_keywords: 
  - "Debug.Goto 命令"
  - "移至命令"
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 移至命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

移動游標至指定行。  
  
## 語法  
  
```  
Edit.GoTo [linenumber]  
```  
  
## 引數  
 `linenumber`  
 選擇項。  整數，表示要移至的行編號。  
  
## 備註  
 行編號從 1 開始。  如果 `linenumber` 的值小於 1，則顯示第一行。  如果 `linenumber` 的值大於最後一行的編號，則顯示最後一行。  
  
 如果未指定 `linenumber` 的值，則顯示 \[**移至行**\] 對話方塊。  
  
 這個命令的別名是 GoToLn。  
  
## 範例  
  
```  
>Edit.GoTo 125  
```  
  
## 請參閱  
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)