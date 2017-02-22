---
title: "搜尋運算式中的進階搜尋運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "說明檢視器 2.0, 搜尋程式碼"
  - "說明檢視器 2.0, 依程式語言搜尋程式碼"
  - "說明檢視器 2.0, 搜尋關鍵字"
  - "說明檢視器 2.0, 搜尋標題"
  - "搜尋程式碼 [說明檢視器 2.0]"
  - "搜尋標題 [說明檢視器 2.0]"
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 搜尋運算式中的進階搜尋運算子
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用進階的搜尋運算子，以便從簡單的運算式建立更複雜的搜尋運算式來精簡搜尋內容。  如下表所示，這些運算子來限制查詢所執行的內容。  
  
> [!WARNING]
>  您必須輸入進階的搜尋運算子最後加冒號而且中間不可有空格，讓搜尋引擎辨識它們。  
  
|若要搜尋|使用|範例|結果|  
|----------|--------|--------|--------|  
|在主題標題中的詞彙|標題:|標題: binaryreader|在標題包含「binaryreader」的主題。|  
|程式碼範例中的詞彙|程式碼：|程式碼: readdouble|在程式碼範例包含「readdouble」的主題。|  
|在特定程式語言的範例中的詞彙|程式碼: vb|程式碼:vb:字串|在 Visual Basic 範例中包含「string」的主題。|  
|與特定索引關鍵字相關聯的主題|關鍵字：|關鍵字: readbyte|與「readbyte」索引關鍵字相關聯的主題。|  
  
 您可以使用此程式碼：運算子用來了解數種程式設計語言的內容，不過它只傳回標記為特定程式語言的內容的結果。  下表列出該運算子支援的程式語言:  
  
|程式語言|使用|  
|----------|--------|  
|Visual Basic|程式碼: vb<br /><br /> 或<br /><br /> code:visualbasic|  
|C\#|程式碼:c\#<br /><br /> 或<br /><br /> 程式碼: csharp|  
|C\+\+|程式碼: cpp<br /><br /> 或<br /><br /> 程式碼:C\+\+<br /><br /> 或<br /><br /> 程式碼:cplusplus|  
|F\#|程式碼:f\#<br /><br /> 或<br /><br /> 程式碼:fsharp|  
|JavaScript|code:javascript<br /><br /> 或<br /><br /> 程式碼:js|  
|XAML|code:xaml|  
  
## 請參閱  
 [搜尋運算式中的邏輯運算子](../ide/logical-operators-in-search-expressions.md)   
 [全文檢索搜尋提示](../ide/full-text-search-tips.md)