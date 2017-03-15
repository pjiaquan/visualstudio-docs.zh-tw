---
title: "HOW TO：搭配使用中斷點與 XSLT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# HOW TO：搭配使用中斷點與 XSLT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可在 XSLT 樣式表或 XML 來源文件中設定中斷點。如果您在標記上設定了中斷點，則在開始執行時，中斷點會移至下一個具有原始程式行資訊的陳述式 \(Statement\)。  
  
 如需詳細資訊，請參閱 [Debugging Basics: Breakpoints](http://msdn.microsoft.com/zh-tw/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)。  
  
## 在樣式表中設定中斷點  
 中斷點可在 XSLT 樣式表的開始標記、結束標記及文字節點上設定。中斷點也可以在指令碼區塊的程式碼上設定。  
  
#### 在樣式表中設定中斷點  
  
1.  在 XML 編輯器中開啟樣式表。  
  
2.  將游標定位於中斷點的位置，按一下滑鼠右鍵，並指向 \[中斷點\] 後，再按一下 \[插入中斷點\]。  
  
3.  按一下文件屬性視窗中 \[**輸入**\] 欄位上的瀏覽按鈕 \(**...**\)。  
  
4.  找出 XML 來源文件，然後按一下 \[**開啟**\]。  
  
     這會設定用於 XSLT 轉換的來源文件檔案。  
  
5.  在 \[XML 編輯器\] 工具列上，按一下 \[**偵錯 XSL**\] 按鈕。  
  
## 在 XML 來源文件中設定中斷點  
 中斷點可以在 XML 來源文件的項目、屬性、命名空間節點、註解、處理指示與文字節點上設定。您無法在文件節點或從父項目繼承的命名空間節點上設定中斷點。  
  
#### 在 XML 來源文件中設定中斷點  
  
1.  在 XML 編輯器中開啟 XML 文件。  
  
2.  將游標定位於中斷點的位置，按一下滑鼠右鍵，並指向 \[**中斷點**\] 後，再按一下 \[**插入中斷點**\]。  
  
3.  按一下文件屬性視窗中 \[**樣式表**\] 欄位上的瀏覽按鈕 \(**...**\)。  
  
4.  找出 XML 來源文件，然後按一下 \[**開啟**\]。  
  
     這會設定用於 XSLT 轉換的來源文件檔案。  
  
5.  在 \[XML 編輯器\] 工具列上，按一下 \[**偵錯 XSL**\] 按鈕。  
  
## 請參閱  
 [逐步解說：偵錯 XSLT 樣式表](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)