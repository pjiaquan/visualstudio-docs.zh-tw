---
title: "疑難排解程式碼片段 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense 程式碼片段, 疑難排解"
  - "IntelliSense 程式碼片段疑難排解"
  - "Visual Basic 疑難排解, IntelliSense 程式碼片段"
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 疑難排解程式碼片段
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

與 IntelliSense 程式碼片段有關的問題通常會由兩個問題所造成：損毀的程式碼片段檔案或程式碼片段檔案中有不正確的內容。  
  
## 常見問題  
  
### 程式碼片段無法從 Visual Studio 原始程式檔的檔案總管拖曳  
  
-   程式碼片段檔案中的 XML 可能已損毀。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的 \[**XML 編輯器**\] 可以找出 XML 結構中的問題。  
  
-   程式碼片段檔案可能不符合程式碼片段結構描述。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的 \[**XML 編輯器**\] 可以找出 XML 結構中的問題。  
  
### 程式碼有未反白顯示的編譯器錯誤  
  
-   您可能遺漏專案參考。  請檢查程式碼片段的相關文件。  如果在電腦上找不到參考，您需要加以安裝。  插入程式碼片段應該將任何需要的參考加入至專案。  如果程式碼片段遺漏參考資訊，可以當做錯誤向程式碼片段建立者報告。  
  
-   可能未定義變數。  應該反白顯示程式碼片段中未定義的變數。  如果沒有，可以當做錯誤向程式碼片段建立者報告。  
  
## 請參閱  
 [程式碼片段](../ide/code-snippets.md)