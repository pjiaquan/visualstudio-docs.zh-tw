---
title: "How to: Search for a Process in Processes View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Processes view"
  - "processes, searching for"
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Process in Processes View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用處理序 ID 或模組字串做為搜尋準則，在 \[處理序\] 檢視中搜尋特定處理序。  您也可以指定搜尋的初始方向。  對話方塊中的欄位會顯示處理序樹狀結構中選取之處理序的屬性。  
  
### 若要在處理序檢視中搜尋處理序  
  
1.  將視窗排列成可以同時顯示 Spy\+\+ 及作用中的[處理序檢視](../debugger/processes-view.md)視窗。  
  
2.  選擇 \[**搜尋**\] 功能表中的 \[**尋找處理序**\]。  
  
     [處理序搜尋對話方塊](../debugger/process-search-dialog-box.md)隨即開啟。  
  
3.  輸入處理序 ID 或模組字串做為搜尋準則。  
  
4.  清除您不要指定值的任何欄位。  
  
    > [!TIP]
    >  若要尋找模組所擁有的全部處理序，請清除 \[**處理序**\] 方塊，並在 \[**模組**\] 方塊中輸入模組名稱。  然後，使用 \[**找下一個**\] 繼續搜尋處理序。  
  
5.  為搜尋的初始方向選擇 \[**上**\] 或 \[**下**\]。  
  
6.  按一下 \[**確定**\]。  
  
 如果找到符合的處理序，\[**處理序**\] 檢視視窗就會反白顯示處理序。