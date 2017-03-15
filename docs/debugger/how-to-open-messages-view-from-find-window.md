---
title: "如何：從尋找視窗開啟訊息檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Spy++ 中的訊息檢視, 開啟"
  - "開啟 Spy++ 中的訊息檢視"
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# 如何：從尋找視窗開啟訊息檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您會發現使用 \[**尋找視窗**\] 對話方塊來選取目標視窗，接著開啟該視窗的 \[訊息\] 檢視，非常方便。  
  
### 若要使用尋找視窗對話方塊來開啟訊息檢視視窗  
  
1.  將視窗排列成可以同時顯示 Spy\+\+ 及目標視窗。  
  
2.  選擇 \[**Spy**\] 功能表中的 \[**尋找視窗**\]。  
  
     [尋找視窗對話方塊](../debugger/find-window-dialog-box.md)隨即開啟。  
  
3.  從 \[**視窗**\] 索引標籤，將 \[**搜尋工具**\] 拖曳到目標視窗上。  當您拖曳工具時，\[**尋找視窗**\] 對話方塊會顯示選取之視窗的詳細資訊。  
  
     \-或\-  
  
     如果您具有要檢查之視窗的控制代碼 \(例如，從偵錯工具複製\)，可以在 \[**控制代碼**\] 文字方塊中輸入該控制代碼。  
  
4.  選取 \[**顯示**\] 底下的 \[**訊息**\]。  
  
5.  按 \[**確定**\]。  
  
     空白的[訊息檢視](../debugger/messages-view.md)視窗隨即開啟，並且 \[**訊息**\] 功能表會加入至 \[Spy\+\+\] 工具列。  
  
6.  從 \[**訊息**\] 功能表中選擇 \[**記錄選項**\]。  
  
     [訊息選項對話方塊](../debugger/message-options-dialog-box.md)隨即開啟。  
  
7.  選取您要顯示之訊息的選項。  
  
8.  按 \[**確定**\] 開始記錄訊息。  
  
     視所選取的選項而定，訊息會開始資料流處理至作用中的 \[訊息\] 檢視視窗。  
  
9. 當您有足夠的訊息時，選擇 \[**訊息**\] 功能表中的 \[**停止記錄**\]。