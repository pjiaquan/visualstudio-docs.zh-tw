---
title: "如何：使用編輯後繼續 (C#) | Microsoft Docs"
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
  - "編輯後繼續 [C#], 關於編輯後繼續"
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：使用編輯後繼續 (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

利用 C\# 的 \[編輯後繼續\]，偵錯時您可以在中斷模式中變更程式碼。  不需要停止並重新啟動偵錯工作階段，就可以套用這些變更。  
  
 當您在中斷模式中進行變更時，就會自動叫用 \[編輯後繼續\]，然後請選擇偵錯工具執行命令，例如 \[**繼續**\]、\[**逐步執行**\] 或 \[**設定下一個陳述式**\]，或在偵錯視窗中評估函式。  
  
> [!NOTE]
>  偵錯 Compact Framework、最佳化程式碼、機器碼\/Managed 程式碼混合的程式碼，或 SQL Server Common Language Runtime \(CLR\) 整合程式碼時，不支援 \[編輯後繼續\]。  如果您嘗試在上述其中一種情況套用程式碼的變更，偵錯工具會出現一個對話方塊說明不支援 \[編輯後繼續\]。  
  
### 若要自動叫用 \[編輯後繼續\]  
  
1.  請在中斷模式中，對原始程式碼進行變更。  
  
2.  從 \[**偵錯**\] 功能表按一下 \[**繼續**\]、\[**逐步執行**\] 或 \[**設定下一個陳述式**\]，或在偵錯視窗中評估函式。  
  
     這時就會編譯新的程式碼，並以新的程式碼繼續進行偵錯。  \[編輯後繼續\] 不支援某些變更。  如需詳細資訊，請參閱[支援的程式碼變更 \(C\#\)](../debugger/supported-code-changes-csharp.md)。  
  
### 若要啟用\/停用編輯後繼續  
  
1.  在 \[**工具**\] 功能表上，按一下 \[**選項**\]。  
  
2.  在 \[**選項**\] 對話方塊中展開 \[**偵錯**\] 節點，並選取 \[**編輯後繼續**\]。  
  
3.  在 \[**編輯後繼續**\] 頁的 \[**選項**\] 對話方塊中，選取或清除 \[**啟用編輯後繼續**\] 核取方塊。  
  
     當您重新啟動偵錯工作階段時，這些設定便會生效。  
  
## 請參閱  
 [編輯後繼續 \(Visual C\#\)](../debugger/edit-and-continue-visual-csharp.md)   
 [支援的程式碼變更 \(C\#\)](../debugger/supported-code-changes-csharp.md)   
 [編輯後繼續的錯誤和警告 \(C\#\)](../misc/edit-and-continue-errors-and-warnings-csharp.md)