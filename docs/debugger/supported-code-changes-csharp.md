---
title: "支援的程式碼變更 (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "編輯後繼續 [C#], 支援的程式碼變更"
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 支援的程式碼變更 (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

\[編輯後繼續\] 會處理方法主體內大多數程式碼的變更。  但是在偵錯期間，無法套用方法主體外的變更和方法主體內的某些變更。  若要套用這些不支援的變更，您必須停止偵錯，然後使用新版程式碼重新啟動偵錯。  
  
 偵錯工作階段期間不能將下列變更套用至 C\# 程式碼：  
  
-   變更目前的陳述式或任何其他使用中陳述式。  
  
     使用中陳述式包含了在呼叫堆疊的函式中，為了取得目前陳述式而呼叫的任何陳述式。  
  
     目前的陳述式在來源視窗中會以黃色背景標示。  其他使用中陳述式會以灰色背景標示，而且是唯讀的。  這些預設色彩可以在 \[**選項**\] 對話方塊中進行變更。  
  
-   變更類型的簽章。  
  
-   加入會擷取之前尚未擷取之變數的匿名方法。  
  
-   加入、移除或變更屬性。  
  
-   加入、移除或變更 `using` 指示詞。  
  
-   在使用中陳述式前後加入 `foreach`、`using` 或 `lock`。  
  
## Unsafe 程式碼  
 變更 Unsafe 程式碼的限制與變更 Safe 程式碼的限制相同，但前者多了下列這一項額外限制：\[編輯後繼續\] 不支援對包含 `stackalloc` 運算子之方法內的 Unsafe 程式碼進行變更。  
  
## 例外狀況  
 \[編輯後繼續\] 支援 `catch` 和 `finally` 區塊的變更，不同之處在於不允許將 `catch` 或 `finally` 區塊加入使用中陳述式前後。  
  
## 不支援的案例  
 \[編輯後繼續\] 無法用於下列偵錯案例中：  
  
-   在某些情況下偵錯 LINQ 程式碼。  如需詳細資訊，請參閱[偵錯 LINQ](../debugger/debugging-linq.md)。  
  
    -   擷取之前尚未擷取的變數。  
  
    -   變更查詢運算式的類型 \(例如，select a \=\> select new { A \= a };\)  
  
    -   移除包含使用中陳述式的 `where`。  
  
    -   移除包含使用中陳述式的 `let`。  
  
    -   移除包含使用中陳述式的 `join`。  
  
    -   移除包含使用中陳述式的 `orderby`。  
  
-   混合模式 \(原生\/Managed\) 偵錯。  
  
-   SQL 偵錯  
  
-   偵錯 Dr.  Watson 傾印。  
  
-   在未選取 \[**發生未處理的例外狀況時回溯呼叫堆疊**\] 選項的情況下，於發生未處理的例外狀況後編輯程式碼。  
  
-   偵錯內嵌的執行階段應用程式。  
  
-   對具有 \[**附加至**\] 的應用程式進行偵錯，而不是從 \[**偵錯**\] 功能表選擇 \[**啟動**\] 執行應用程式。  
  
-   偵錯最佳化程式碼  
  
-   由於建置錯誤以致新版本建置失敗之後，對舊版程式碼進行偵錯。  
  
## 請參閱  
 [編輯後繼續 \(Visual C\#\)](../debugger/edit-and-continue-visual-csharp.md)   
 [如何：使用編輯後繼續 \(C\#\)](../debugger/how-to-use-edit-and-continue-csharp.md)