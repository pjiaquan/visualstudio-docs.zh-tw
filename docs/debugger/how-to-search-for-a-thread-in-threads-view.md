---
title: "How to: Search for a Thread in Threads View | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threads, searching"
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# How to: Search for a Thread in Threads View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用執行緒 ID 或模組字串做為搜尋準則，在 \[執行緒\] 檢視中搜尋特定執行緒。  您也可以指定搜尋的初始方向。  對話方塊中的欄位會顯示執行緒樹狀結構中選取之執行緒的屬性。  
  
### 若要在執行緒檢視中搜尋執行緒  
  
1.  將視窗排列成可以同時顯示 Spy\+\+ 及作用中的[執行緒檢視](../debugger/threads-view.md)視窗。  
  
2.  選擇 \[**搜尋**\] 功能表中的 \[**尋找執行緒**\]。  
  
     [執行緒搜尋對話方塊](../debugger/thread-search-dialog-box.md)隨即開啟。  
  
3.  輸入執行緒 ID 或模組字串做為搜尋準則。  
  
4.  清除您不要指定值的任何欄位。  
  
    > [!TIP]
    >  若要尋找模組所擁有的全部執行緒，請清除 \[**執行緒**\] 文字方塊，並在 \[**模組**\] 方塊中輸入模組名稱。  然後，使用 \[**找下一個**\] 繼續搜尋執行緒。  
  
5.  為搜尋的初始方向選擇 \[**上**\] 或 \[**下**\]。  
  
6.  按一下 \[**確定**\]。  
  
 如果找到符合的執行緒，\[執行緒\] 檢視視窗就會反白顯示執行緒。