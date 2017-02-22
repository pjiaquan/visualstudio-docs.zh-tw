---
title: "訊息選項對話方塊、訊息索引標籤 | Microsoft Docs"
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
  - "訊息選項, 訊息"
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 訊息選項對話方塊、訊息索引標籤
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 \[**訊息**\] 索引標籤，可以選取哪些訊息類型要列在[訊息檢視](../debugger/messages-view.md)中，以及指定訊息搜尋準則。  若要顯示[訊息選項對話方塊](../debugger/message-options-dialog-box.md)，請選擇 \[**監視**\] 功能表上的 \[**記錄檔訊息** \]。  
  
 通常，您要先選取 \[**訊息群組**\]，然後選取個別 \[**要檢視的訊息**\] 以微調選項。  \[**全部**\] 按鈕會選取所有訊息類型，而 \[**無**\] 按鈕則會清除所有類型。  
  
 \[**訊息**\] 索引標籤中的可用設定如下：  
  
 **要檢視的訊息**  
 選取要檢視的特定訊息。  當您建立新的 \[訊息\] 視窗時，該視窗會顯示所有的訊息。  當您從 \[**訊息**\] 索引標籤篩選訊息時，這個篩選條件只會套用至新的訊息，而不會套用至已經顯示在 \[視窗\] 檢視中的訊息。  
  
 **訊息群組**  
 選取要檢視的訊息群組。  可用群組包括：  
  
-   WM\_USER：含有大於或等於 WM\_USER 的代碼  
  
-   已註冊：已向 **RegisterWindowMessage** 呼叫註冊  
  
-   未知：範圍 0 到 \(WM\_USER – 1\) 的未知訊息  
  
 請注意，這些 \[**訊息群組**\] 不會對應至 \[**要檢視的訊息**\] 底下的特定項目。  當您選取群組時，該選項會直接套用至訊息資料流。  
  
 \[**訊息群組**\] 內的灰色核取方塊，代表該群組中的 \[**要檢視的訊息**\] 清單方塊已針對訊息修改過，該群組中並非所有訊息類型都已選取。  
  
 **將設定另存成預設值**  
 儲存目前設定以供日後做為訊息搜尋選項。  當結束 Spy\+\+ 時，這些設定也會儲存起來。