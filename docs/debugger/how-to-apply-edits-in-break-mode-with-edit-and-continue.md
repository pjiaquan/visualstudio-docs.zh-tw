---
title: "如何：以編輯後繼續在中斷模式套用編輯 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.variables.failededit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
helpviewer_keywords: 
  - "中斷模式, 套用程式碼變更"
  - "程式碼, 在中斷模式中編輯"
  - "程式碼, 在中斷模式中編輯"
  - "編輯後繼續 [Visual Basic], 在中斷模式套用編輯"
  - "編輯後繼續, 在中斷模式套用編輯"
  - "編輯, 中斷模式"
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# 如何：以編輯後繼續在中斷模式套用編輯
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在中斷模式中使用 \[編輯後繼續\] 編輯程式碼，並繼續進行而不需停止及重新啟動執行。  
  
 \[編輯後繼續\] 無法用於下列偵錯案例中：  
  
-   混合模式 \(原生\/Managed\) 偵錯。  
  
-   SQL 偵錯  
  
-   偵錯 Dr.  Watson 傾印。  
  
-   在未選取 \[**發生未處理的例外狀況時回溯呼叫堆疊**\] 選項的情況下，於發生未處理的例外狀況後編輯程式碼。  
  
-   偵錯內嵌的執行階段應用程式。  
  
-   使用 \[**附加至**\] 偵錯應用程式，而不使用 \[**偵錯**\] 功能表中的 \[**啟動**\] 執行應用程式。  
  
-   偵錯最佳化程式碼  
  
-   當目標為 64 位元應用程式時，偵錯 Managed 程式碼。  如果要使用 \[編輯後繼續\]，就必須將目標設定為 x86   \(\[*專案*屬性\]、\[編譯\] 索引標籤、\[進階編譯器\] 設定。\)  
  
-   由於建置錯誤以致新版本建置失敗之後，請偵錯舊版的程式碼。  
  
### 在中斷模式中編輯程式碼  
  
1.  執行下列其中一種方法進入中斷模式  
  
    -   在程式碼中設定中斷點，然後從 \[**偵錯**\] 功能表中選擇 \[**開始偵錯**\]，並等待應用程式叫用中斷點。  
  
         \-或\-  
  
    -   開始偵錯，然後從 \[**偵錯**\] 功能表中選取 \[**全部中斷**\]。  
  
         \-或\-  
  
    -   發生例外狀況時，請在 \[**例外狀況助理**\] 中選擇 \[**啟用編輯**\]。  
  
2.  進行想要並正確的程式碼變更。  
  
     如需詳細資訊，請參閱[Visual Basic 編輯後繼續中不支援的編輯](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)。  
  
    > [!NOTE]
    >  如果您嘗試進行 \[編輯後繼續\] 不允許的程式碼變更，您的編輯會被加上紫色波浪線，而且 \[工作清單\] 中會出現工作。  除非您復原不合法的程式碼變更，否則將無法繼續執行程式碼。  
  
3.  在 \[**偵錯**\] 功能表上，按一下 \[**繼續**\] 以恢復偵錯。  
  
     這時程式碼便會一併執行您套用至專案的編輯。  
  
## 請參閱  
 [Visual Basic 編輯後繼續中不支援的編輯](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [編輯後繼續 \(Visual Basic\)](../debugger/edit-and-continue-visual-basic.md)