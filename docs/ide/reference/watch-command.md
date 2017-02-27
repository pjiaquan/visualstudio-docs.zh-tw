---
title: "Watch 命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.watch"
helpviewer_keywords: 
  - "Debug.Watch 命令"
  - "Watch 命令"
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Watch 命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

建立並開啟 \[**監看員**\] 視窗的指定執行個體。  您可以使用 \[**監看員**\] 視窗來計算變數、運算式和暫存器的值，以編輯這些數值並儲存結果。  
  
## 語法  
  
```  
Debug.Watch[index]  
```  
  
## 引數  
 `index`  
 必要項。  監看員視窗的執行個體數目。  
  
## 備註  
 `index` 必須是整數。  有效值為 1、2、3 或 4。  
  
## 範例  
  
```  
>Debug.Watch1  
```  
  
## 請參閱  
 [\[自動變數\] 和 \[區域變數\] 視窗](../Topic/Autos%20and%20Locals%20Windows.md)   
 [如何：編輯變數視窗中的值](../Topic/How%20to:%20Edit%20a%20Value%20in%20a%20Variable%20Window.md)   
 [如何：使用快速監看式對話方塊](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)   
 [命令視窗](../../ide/reference/command-window.md)   
 [尋找\/命令方塊](../../ide/find-command-box.md)   
 [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)