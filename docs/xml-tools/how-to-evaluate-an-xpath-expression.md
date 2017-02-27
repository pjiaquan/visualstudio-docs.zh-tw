---
title: "HOW TO：評估 XPath 運算式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# HOW TO：評估 XPath 運算式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 \[快速監看式\] 對話方塊來評估 XPath 運算式。根據 W3C XPath 1.0 版建議事項，XPath 運算式必須有效。目前的 XSLT 內容 \(即 \[本機\] 視窗中的 `self::node()` 節點\) 提供 XPath 運算式的評估內容。  
  
 下列清單說明當評估 XPath 運算式時，支援哪些函式：  
  
-   支援內建 XPath 函式。  
  
-   不支援內建 XSLT 函式。  
  
-   不支援使用者定義函式。  
  
> [!NOTE]
>  下列程序使用 [逐步解說：偵錯 XSLT 樣式表](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) 主題中的 belowAvg.xsl 及 books.xml 檔案。  
  
### 評估 XPath 運算式  
  
1.  在 `xsl:if` 開始標記處插入中斷點。  
  
2.  在 \[XML 編輯器\] 工具列上，按一下 \[偵錯 XSL\] 按鈕。  
  
     偵錯工具會啟動，並在 `xsl:if` 標記處中斷。  
  
3.  按一下滑鼠右鍵，並選取 \[快速監看式\]。  
  
     會顯示 \[快速監看式\] 對話方塊。  
  
4.  在 \[快速監看式\] 對話方塊的 \[運算式\] 欄位中，輸入 `./price/text()`，並按一下 \[重新評估\]。  
  
     目前書籍節點的價格會出現在 \[值\] 方塊中。  
  
5.  將 XPath 運算式變為 `./price/text() < $bookAverage`，並按一下 \[重新評估\]。  
  
     \[值\] 方塊會顯示 XPath 運算式評估為 `true`。  
  
## 請參閱  
 [偵錯 XSLT](../xml-tools/debugging-xslt.md)