---
title: "快速監看式命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.quickwatch"
helpviewer_keywords: 
  - "Debug.Quickwatch 命令"
  - "快速監看式命令"
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 快速監看式命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在 [快速監看式對話方塊](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md) 的運算式欄位中，顯示選取或指定的文字。  您可以使用此對話方塊計算偵錯工具所辨認之變數的目前值或運算式，或暫存器的內容。  此外，您可以變更任何非常數變數的值或任何暫存器的內容。  
  
## 語法  
  
```  
Debug.QuickWatchq [text]  
```  
  
## 引數  
 `text`  
 選擇項。  要加入至 \[**快速監看式**\] 對話方塊的文字。  
  
## 備註  
 如果省略 `text`，則將目前選取的文字或游標所在的文字加入至 \[監看員\] 視窗。  
  
## 範例  
  
```  
>Debug.QuickWatch  
```  
  
## 請參閱  
 [如何：使用快速監看式對話方塊](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)